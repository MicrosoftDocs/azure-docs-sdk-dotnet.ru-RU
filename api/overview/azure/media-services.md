---
title: Библиотеки служб мультимедиа Azure для .NET
description: Справочник по библиотекам служб мультимедиа Azure для .NET
keywords: Azure, .NET, SDK, API, Media Services
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: media-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: ec6a7ec7f8f0c416d93aad5c91ece4d3b499fd7a
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065404"
---
# <a name="azure-media-services-libraries-for-net"></a><span data-ttu-id="d4a9c-104">Библиотеки служб мультимедиа Azure для .NET</span><span class="sxs-lookup"><span data-stu-id="d4a9c-104">Azure Media Services libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="d4a9c-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="d4a9c-105">Overview</span></span>

<span data-ttu-id="d4a9c-106">Службы мультимедиа Azure — это расширяемая облачная платформа, которая позволяет разработчикам создавать масштабируемые приложения для управления и доставки файлов мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-106">Microsoft Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="d4a9c-107">С помощью служб мультимедиа Azure можно безопасно передавать, сохранять, кодировать и упаковывать видео- или аудиосодержимое для потоковой трансляции разным клиентам (например, на ТВ, ПК и мобильные устройства) или для трансляции по требованию.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span> 

<span data-ttu-id="d4a9c-108">Дополнительные сведения см. в разделе с [общими сведениями](/azure/media-services/media-services-overview) и статье о [начале работы с .NET](/azure/media-services/media-services-dotnet-how-to-use).</span><span class="sxs-lookup"><span data-stu-id="d4a9c-108">To learn more, see [Overview](/azure/media-services/media-services-overview) and [Getting started with .NET](/azure/media-services/media-services-dotnet-how-to-use).</span></span> 

## <a name="client-library"></a><span data-ttu-id="d4a9c-109">Клиентская библиотека</span><span class="sxs-lookup"><span data-stu-id="d4a9c-109">Client library</span></span>

<span data-ttu-id="d4a9c-110">Библиотека пакета SDK служб мультимедиа Azure для .NET позволяет разрабатывать программы в службах мультимедиа с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-110">The Azure Media Services .NET SDK library enables you to program against Media Services using .NET.</span></span> <span data-ttu-id="d4a9c-111">Используйте клиентскую библиотеку служб мультимедиа Azure для подключения, проверки подлинности и разработки с помощью API служб мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-111">Use the Azure Media Services client library to connect, authenticate, and develop against Media Services APIs.</span></span>  

<span data-ttu-id="d4a9c-112">Дополнительные сведения см. в статье [Приступая к работе с доставкой содержимого по запросу с помощью пакета SDK для .NET](/azure/media-services/media-services-dotnet-get-started).</span><span class="sxs-lookup"><span data-stu-id="d4a9c-112">For more information, see [Get started with delivering content on demand using .NET SDK](/azure/media-services/media-services-dotnet-get-started).</span></span>

<span data-ttu-id="d4a9c-113">Установите [пакет NuGet](https://www.nuget.org/packages/windowsazure.mediaservices) непосредственно из [консоли диспетчера пакетов][PackageManager] Visual Studio или с помощью [.NET Core CLI][DotNetCLI].</span><span class="sxs-lookup"><span data-stu-id="d4a9c-113">Install the [NuGet package](https://www.nuget.org/packages/windowsazure.mediaservices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d4a9c-114">Диспетчер пакетов Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d4a9c-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a><span data-ttu-id="d4a9c-115">Пример кода</span><span class="sxs-lookup"><span data-stu-id="d4a9c-115">Code Example</span></span>

<span data-ttu-id="d4a9c-116">В следующем примере кода пакет SDK служб мультимедиа используется для выполнения следующих задач.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-116">The following code example uses Media Services .NET SDK to perform the following tasks:</span></span>

- <span data-ttu-id="d4a9c-117">Создание задания кодирования.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-117">Create an encoding job.</span></span>
- <span data-ttu-id="d4a9c-118">Получение ссылки на стандартный кодировщик мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-118">Get a reference to the Media Encoder Standard encoder.</span></span>
- <span data-ttu-id="d4a9c-119">Указание предустановки для адаптивной потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-119">Specify to use the Adaptive Streaming preset.</span></span>
- <span data-ttu-id="d4a9c-120">Добавление одной задачи кодирования в задание.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-120">Add a single encoding task to the job.</span></span>
- <span data-ttu-id="d4a9c-121">Указание входного ресурса-контейнера для кодирования.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-121">Specify the input asset to be encoded.</span></span>
- <span data-ttu-id="d4a9c-122">Создание выходного ресурса для получения закодированного ресурса.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-122">Create an output asset to receive the encoded asset.</span></span>
- <span data-ttu-id="d4a9c-123">Отправка задания.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-123">Submit the job.</span></span>


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
> [<span data-ttu-id="d4a9c-124">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="d4a9c-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a><span data-ttu-id="d4a9c-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="d4a9c-125">Samples</span></span>

- <span data-ttu-id="d4a9c-126">[Use Azure Media Services to Stream your HLS content Protected with Apple FairPlay](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/) (Использование служб мультимедиа для потоковой передачи содержимого HLS, защищенного с помощью Apple FairPlay)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-126">[Stream your HLS content Protected with Apple FairPlay](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/)</span></span>
- <span data-ttu-id="d4a9c-127">[Copy blobs into an Azure Media Services asset](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/) (Копирование большого двоичного объекта в ресурс служб мультимедиа Azure)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-127">[Copy blob into an Azure Media Services asset using .NET SDK Extensions](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/)</span></span>
- <span data-ttu-id="d4a9c-128">[Encode and Deliver a Live Stream with Azure Media Services using .NET SDK](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/) (Кодирование и доставка данных Live Stream при помощи служб мультимедиа Azure с использованием пакета SDK для .NET)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-128">[Encode and Deliver a Live Stream with Azure Media Services using .NET SDK](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/)</span></span>

<span data-ttu-id="d4a9c-129">Просмотрите [полный список](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) примеров служб мультимедиа Azure.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-129">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) of Azure Media Services samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
