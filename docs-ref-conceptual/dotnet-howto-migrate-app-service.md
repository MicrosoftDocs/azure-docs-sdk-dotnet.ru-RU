---
title: Перенос веб-приложения или службы .NET в Службу приложений Azure
description: Узнайте, как перенести веб-приложение или службу .NET из локальной среды в Службу приложений Azure.
ms.date: 08/11/2018
ms.service: app-service
ms.openlocfilehash: cee1745f64a575836bbf54eca435ba19b508f94c
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190737"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Перенос веб-приложения или службы .NET в Службу приложений Azure 

[Служба приложений](https://docs.microsoft.com/azure/app-service/app-service-web-overview#why-use-web-apps) — это полностью управляемая вычислительная платформа, оптимизированная для размещения масштабируемых веб-сайтов и веб-приложений. В этом документе содержатся сведения о переносе существующего приложения в службу приложений Azure методом lift-and-shift, рекомендуемых изменениях и дополнительных ресурсах для перемещения в облако. Большинство веб-сайтов ASP.NET (WebForms, MVC) и служб (веб-API, WCF) можно переместить в Службу приложений Azure без каких-либо изменений. Для некоторых могут потребоваться незначительные изменения, в то время как для других может понадобиться рефакторинг.

Готовы начать работу? [Опубликуйте свое приложение ASP.NET + SQL в службе приложений Azure](https://go.microsoft.com/fwlink/?linkid=863214).

## <a name="considerations"></a>Рекомендации

### <a name="on-premises-resources-including-sql-server"></a>Локальные ресурсы (включая SQL Server)

Проверьте доступ к локальным ресурсам, так как их, возможно, потребуется перенести или изменить. Вот несколько вариантов действий для упрощения доступа к локальным ресурсам:

* С помощью службы [Виртуальная сеть Azure](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet) создайте сеть VPN для подключения Службы приложений к локальным ресурсам.
* С помощью [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it) предоставьте облаку защищенный доступ к локальным службам, не внося изменения в брандмауэр.
* Перенесите зависимости в Azure (например, [базу данных SQL](https://go.microsoft.com/fwlink/?linkid=863217)).
* Для уменьшения количества зависимостей используйте облачные решения типа "платформа как услуга". Например, вместо подключения к локальному почтовому серверу используйте [SendGrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email). 

### <a name="port-bindings"></a>Привязки портов

Служба приложений Azure поддерживает порт 80 для HTTP-трафика и порт 443 для HTTPS-трафика.

Для WCF поддерживаются такие привязки:

Привязка | Примечания
--------|--------
BasicHttp | 
WSHttp | 
WSDualHttpBinding | Необходимо включить [поддержку веб-сокетов](https://docs.microsoft.com/azure/app-service/web-sites-configure).
NetHttpBinding | Необходимо включить [поддержку веб-сокетов](https://docs.microsoft.com/azure/app-service/web-sites-configure) для дуплексных контрактов.
NetHttpsBinding | Необходимо включить [поддержку веб-сокетов](https://docs.microsoft.com/azure/app-service/web-sites-configure) для дуплексных контрактов.
BasicHttpContextBinding |
WebHttpBinding |
WSHttpContextBinding |

### <a name="authentication"></a>Authentication

Служба приложений Azure поддерживает анонимную аутентификацию по умолчанию. При необходимости можно настроить аутентификацию с помощью форм. Аутентификация Windows может использоваться только при интеграции с Azure Active Directory и ADFS. [Подробнее об интеграции локальных каталогов с Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Сборки в глобальном кэше сборок (GAC) 

Эта возможность не поддерживается. Рекомендуется скопировать необходимые сборки в папку приложения `\bin`. Установленные на сервере пользовательские пакеты MSI (например, генераторы PDF и т. п.) использовать нельзя.  

### <a name="iis-settings"></a>Параметры служб IIS
Теперь все параметры приложения, которые традиционно настраиваются с помощью файла applicationHost.config, можно настроить на портале Azure. Это касается разрядности пула приложений, включения и отключения протокола WebSocket, версии управляемого конвейера, версии платформы .NET Framework (2.0 или 4.0) и других параметров. Чтобы изменить [параметры приложения](https://docs.microsoft.com/azure/app-service/web-sites-configure), перейдите на [портал Azure](https://portal.azure.com), откройте колонку нужного веб-приложения и выберите вкладку **Параметры приложения**.

#### <a name="iis5-compatibility-mode"></a>Режим совместимости с IIS5
Режим совместимости с IIS5 не поддерживается. В Службе приложений Azure каждое веб-приложение и все располагающиеся под ним приложения выполняются в одном и том же рабочем процессе с определенным набором [пула приложений](http://technet.microsoft.com/library/cc735247(v=WS.10).aspx).

#### <a name="iis7-schema-compliance"></a>Соответствие схеме IIS7+  
Некоторые элементы и атрибуты не определены в схеме IIS Службы приложений Azure. При возникновении проблем рекомендуется использовать [преобразования XDT](http://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).

#### <a name="single-application-pool-per-site"></a>Один пул приложений на сайт  
В Службе приложений Azure каждое веб-приложение и все располагающиеся под ним приложения выполняются в одном и том же пуле приложений. Рекомендуем создать один пул приложений с общими настройками или для каждого приложения создать отдельное веб-приложение.

### <a name="com-and-com-components"></a>Компоненты COM и COM+  
Служба приложений Azure не разрешает регистрацию COM-компонентов на платформе. Если в приложении используются какие-либо COM-компоненты, их необходимо переписать в формате управляемого кода и развернуть вместе с сайтом или приложением.  

### <a name="physical-directories"></a>Физические каталоги 
Служба приложений Azure не разрешает доступ к физическим дискам. Для доступа к файлам по протоколу SMB, возможно, потребуется использовать службу [Файлы Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction). Доступ к файлам в [хранилище BLOB-объектов Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) осуществляется по протоколу HTTPS.  

### <a name="isapi-filters"></a>Фильтры ISAPI  
Служба приложений Azure может поддерживать использование фильтров ISAPI, но для этого вместе с сайтом необходимо развернуть DLL-библиотеку ISAPI и зарегистрировать ее с помощью файла web.config.  

### <a name="https-bindings-and-ssl"></a>HTTPS-привязки и SSL 
HTTPS-привязки перенесены не будут, так же как и связанные с веб-сайтами SSL-сертификаты, но после переноса сайта [SSL-сертификаты можно будет передать вручную](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl).  

### <a name="sharepoint-and-frontpage"></a>SharePoint и FrontPage 
Расширения SharePoint и серверные расширения FrontPage (FPSE) не поддерживаются.

### <a name="web-site-size"></a>Размер веб-сайта  
Максимальный размер содержимого на бесплатном сайте не должен превышать 1 ГБ. Если размер сайта превышает 1 ГБ, необходимо перейти на платный SKU. См. [цены на Службу приложений](https://azure.microsoft.com/pricing/details/app-service/windows/). 

### <a name="database-size"></a>Размер базы данных  
Для баз данных SQL Server см. [цены на Базу данных SQL](http://azure.microsoft.com/pricing/details/sql-database).  

### <a name="azure-active-directory-aad-integration"></a>Интеграция с Azure Active Directory (AAD)  
AAD не работает с бесплатными приложениями. Для использования AAD необходимо перевести приложение на платный SKU. См. [цены на Службу приложений](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Мониторинг и диагностика.
Решения для мониторинга и диагностики, которые вы используете сейчас в локальной среде, вряд ли будут работать в облаке. Но Azure предоставляет средства для ведения журнала, мониторинга и диагностики, позволяющие определять и устранять проблемы, связанные с веб-приложениями. Диагностику веб-приложения можно без труда включить в его конфигурации, а записи журналов доступны для просмотра в Azure Application Insights. [Подробнее о включении ведения журнала диагностики для веб-приложений](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Строки подключения и параметры приложения
Рекомендуется использовать [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/). Это служба, в которой надежно хранятся конфиденциальные сведения, используемые в вашем приложении. Кроме того, эти данные можно хранить в настройках службы приложений.

### <a name="dns"></a>DNS
Возможно, вам понадобится обновить конфигурацию DNS в соответствии с требованиями приложения. Эти параметры DNS можно настроить в [параметрах личного домена](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain) службы приложений. 

## <a name="azure-app-service-with-windows-containers"></a>Служба приложений Azure с контейнерами Windows
Если приложение не удается перенести непосредственно в Службу приложений, попробуйте воспользоваться Службой приложений с контейнерами Windows. Это даст возможность использовать GAC, COM-компоненты, пакеты MSI, даст полный доступ к API-интерфейсам .NET FX, DirectX и др.

## <a name="additional-reading"></a>Дополнительные материалы

* [Как определить, соответствует ли ваше приложение требованиям службы приложений?](https://azure.microsoft.com/downloads/migration-assistant/)
* [Перенос базы данных в облако.](https://go.microsoft.com/fwlink/?linkid=863217)
* [Сведения о песочнице веб-приложений Azure и ее ограничениях.](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)

## <a name="next-steps"></a>Дополнительная информация

> [!div class="nextstepaction"]
> [Развертывание приложения из Visual Studio](https://docs.microsoft.com/visualstudio/deployment/quickstart-deploy-to-azure?view=vs-2017)
