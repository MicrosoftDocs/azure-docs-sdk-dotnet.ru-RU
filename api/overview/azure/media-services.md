---
title: Библиотеки служб мультимедиа Azure для .NET
description: Справочник по библиотекам служб мультимедиа Azure для .NET
ms.date: 10/19/2017
ms.topic: reference
ms.service: media-services
ms.openlocfilehash: cbb37d5d80c152ef53dba14c83cf2a2695e6b0f0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190587"
---
# <a name="azure-media-services-libraries-for-net"></a>Библиотеки служб мультимедиа Azure для .NET

## <a name="overview"></a>Обзор

Службы мультимедиа Azure — это расширяемая облачная платформа, которая позволяет разработчикам создавать масштабируемые приложения для управления и доставки файлов мультимедиа. С помощью служб мультимедиа Azure можно безопасно передавать, сохранять, кодировать и упаковывать видео- или аудиосодержимое для потоковой трансляции разным клиентам (например, на ТВ, ПК и мобильные устройства) или для трансляции по требованию. 

Дополнительные сведения см. в разделе с [общими сведениями](/azure/media-services/media-services-overview) и статье о [начале работы с .NET](/azure/media-services/media-services-dotnet-how-to-use). 

## <a name="client-library"></a>Клиентская библиотека

Библиотека пакета SDK служб мультимедиа Azure для .NET позволяет разрабатывать программы в службах мультимедиа с помощью .NET. Используйте клиентскую библиотеку служб мультимедиа Azure для подключения, проверки подлинности и разработки с помощью API служб мультимедиа.  

Дополнительные сведения см. в статье [Приступая к работе с доставкой содержимого по запросу с помощью пакета SDK для .NET](/azure/media-services/media-services-dotnet-get-started).

Установите [пакет NuGet](https://www.nuget.org/packages/windowsazure.mediaservices) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].

#### <a name="visual-studio-package-manager"></a>Диспетчер пакетов Visual Studio

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a>Пример кода

В следующем примере кода пакет SDK служб мультимедиа используется для выполнения следующих задач.

- Создание задания кодирования.
- Получение ссылки на стандартный кодировщик мультимедиа.
- Указание предустановки для адаптивной потоковой передачи.
- Добавление одной задачи кодирования в задание.
- Указание входного ресурса-контейнера для кодирования.
- Создание выходного ресурса для получения закодированного ресурса.
- Отправка задания.


```csharp
/* Include this 'using' directive:
using Microsoft.WindowsAzure.MediaServices.Client;
*/

CloudMediaContext context = new CloudMediaContext(new Uri(mediaServiceRESTAPIEndpoint), tokenProvider);

// Get an uploaded asset.
IAsset asset = context.Assets.FirstOrDefault();

// Encode and generate the output using the "Adaptive Streaming" preset.
// Declare a new job.
IJob job = context.Jobs.Create("Media Encoder Standard Job");
// Get a media processor reference, and pass to it the name of the 
// processor to use for the specific task.
IMediaProcessor processor = context.MediaProcessors.Where(p => p.Name == mediaProcessorName)
    .ToList().OrderBy(p => new Version(p.Version)).LastOrDefault();
if (processor == null) 
{
    throw new ArgumentException(string.Format("Unknown media processor", mediaProcessorName));
}

// Create a task with the encoding details, using a string preset.
// In this case "Adaptive Streaming" preset is used.
ITask task = job.Tasks.AddNew("My encoding task", processor, "Adaptive Streaming", TaskOptions.None);

// Specify the input asset to be encoded.
task.InputAssets.Add(asset);
// Add an output asset to contain the results of the job. 
// This output is specified as AssetCreationOptions.None, which 
// means the output asset is not encrypted. 
task.OutputAssets.AddNew("Output asset", AssetCreationOptions.None);

job.Submit();
job.GetExecutionProgressTask(CancellationToken.None).Wait();
```

> [!div class="nextstepaction"]
> [Обзор клиентских API-интерфейсов](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a>Примеры

- [Use Azure Media Services to Stream your HLS content Protected with Apple FairPlay](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/) (Использование служб мультимедиа для потоковой передачи содержимого HLS, защищенного с помощью Apple FairPlay)
- [Copy blobs into an Azure Media Services asset](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/) (Копирование большого двоичного объекта в ресурс служб мультимедиа Azure)
- [Encode and Deliver a Live Stream with Azure Media Services using .NET SDK](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/) (Кодирование и доставка данных Live Stream при помощи служб мультимедиа Azure с использованием пакета SDK для .NET)

Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) примеров служб мультимедиа Azure.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
