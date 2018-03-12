---
title: "dotnet CLI を使用して NuGet パッケージを作成し公開するための入門ガイド | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 01/24/2018
ms.topic: get-started-article
ms.prod: nuget
ms.technology: 
description: ".NET Core CLI (dotnet) を使用した NuGet パッケージの作成と公開に関するチュートリアル。"
keywords: "NuGet パッケージの作成、NuGet パッケージの公開、NuGet チュートリアル、NuGet パッケージの dotnet publish"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c9f46cafafcdc238e43979d6f05521e19bf3d7f6
ms.sourcegitcommit: eabd401616a98dda2ae6293612acb3b81b584967
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="create-and-publish-a-package"></a><span data-ttu-id="2a8fd-104">パッケージの作成と公開</span><span class="sxs-lookup"><span data-stu-id="2a8fd-104">Create and publish a package</span></span>

<span data-ttu-id="2a8fd-105">これは、`dotnet`コマンド ライン インターフェイス (CLI) を使用して、.NET クラス ライブラリから NuGet パッケージを作成し、nuget.org に公開する簡単なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-105">It's a simple process to create a NuGet package from a .NET Class Library and publish it to nuget.org using the `dotnet` command-line interface (CLI).</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="2a8fd-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="2a8fd-106">Pre-requisites</span></span>

1. <span data-ttu-id="2a8fd-107">`dotnet` CLI を含む [.NET Core SDK](https://www.microsoft.com/net/download/) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-107">Install the [.NET Core SDK](https://www.microsoft.com/net/download/), which includes the `dotnet` CLI.</span></span>

1. <span data-ttu-id="2a8fd-108">まだ持っていない場合は、[nuget.org で無料アカウントを登録](https://www.nuget.org/users/account/LogOn?returnUrl=%2F)します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-108">[Register for a free account on nuget.org](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) if you don't have one already.</span></span> <span data-ttu-id="2a8fd-109">新しいアカウントを作成すると、確認メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-109">Creating a new account sends a confirmation email.</span></span> <span data-ttu-id="2a8fd-110">パッケージをアップロードするには、その前にアカウントを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-110">You must confirm the account before you can upload a package.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="2a8fd-111">クラス ライブラリ プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-111">Create a class library project</span></span>

<span data-ttu-id="2a8fd-112">パッケージ化するコードに既存の .NET クラス ライブラリ プロジェクトを使用することも、次の手順に従って単純なプロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-112">You can use an existing .NET Class Library project for the code you want to package, or create a simple one as follows:</span></span>

1. <span data-ttu-id="2a8fd-113">`AppLogger`という名前のフォルダーを作成し、そこに変更します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-113">Create a folder called `AppLogger` and change into it.</span></span>

1. <span data-ttu-id="2a8fd-114">`dotnet new classlib`を使用してプロジェクトを作成します。プロジェクト名には現在のフォルダーの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-114">Create the project using `dotnet new classlib`, which uses the name of the current folder for the project.</span></span>

## <a name="add-package-metadata-to-the-project-file"></a><span data-ttu-id="2a8fd-115">パッケージのメタデータをプロジェクト ファイルに追加する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-115">Add package metadata to the project file</span></span>

<span data-ttu-id="2a8fd-116">すべての NuGet パッケージには、その内容と依存関係を説明するマニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-116">Every NuGet package needs a manifest that describes the package's contents and dependencies.</span></span> <span data-ttu-id="2a8fd-117">最終的なパッケージでは、マニフェストは、プロジェクト ファイルに含まれる NuGet メタデータのプロパティから生成される `.nuspec` ファイルです。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-117">In a final package, the manifest is a `.nuspec` file that is generated from the NuGet metadata properties that you include in the project file.</span></span>

1. <span data-ttu-id="2a8fd-118">プロジェクト ファイル (`.csproj`) を開いて、既存の `<PropertyGroup>` タグ内に次の最小限のプロパティを追加し、必要に応じて値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-118">Open your project file (`.csproj`) and add the following minimal properties inside the exiting `<PropertyGroup>` tag, changing the values as appropriate:</span></span>

    ```xml
    <PackageId>AppLogger</PackageId>
    <Version>1.0.0</Version>
    <Authors>your_name</Authors>
    <Company>your_company</Company>
    ```

    > [!Important]
    > <span data-ttu-id="2a8fd-119">パッケージに、nuget.org または使用しているホスト全体で一意の識別子を付けます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-119">Give the package an identifier that's unique across nuget.org or whatever host you're using.</span></span> <span data-ttu-id="2a8fd-120">このチュートリアルでは、以降の公開手順でパッケージを一般公開するので (ただし、誰かが実際に使用する可能性はありません)、名前に "Sample" または "Test" を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-120">For this walkthrough we recommend including "Sample" or "Test" in the name as the later publishing step does make the package publicly visible (though it's unlikely anyone will actually use it).</span></span>

1. <span data-ttu-id="2a8fd-121">「[NuGet メタデータ プロパティ](/dotnet/core/tools/csproj#nuget-metadata-properties)」で説明する省略可能なプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-121">Add any optional properties described on [NuGet metadata properties](/dotnet/core/tools/csproj#nuget-metadata-properties).</span></span>

    > [!Note]
    > <span data-ttu-id="2a8fd-122">公開用にビルドされたパッケージの場合は、**PackageTags**プロパティに特に注意してください。これらのタグは他のユーザーがパッケージを検索して、パッケージの動作を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-122">For packages built for public consumption, pay special attention to the **PackageTags** property, as tags help others find your package and understand what it does.</span></span>

## <a name="run-the-pack-command"></a><span data-ttu-id="2a8fd-123">pack コマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-123">Run the pack command</span></span>

<span data-ttu-id="2a8fd-124">プロジェクトから NuGet パッケージ (`.nupkg` ファイル) をビルドするには、`dotnet pack` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-124">To build a NuGet package (a `.nupkg` file) from the project, run the `dotnet pack` command:</span></span>

```cli
# Uses the project file in the current folder by default
dotnet pack
```

<span data-ttu-id="2a8fd-125">出力に、`.nupkg` ファイルへのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-125">The output will show the path to the `.nupkg` file:</span></span>

```output
Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 29.91 ms for D:\proj\AppLoggerNet\AppLogger\AppLogger.csproj.
  AppLogger -> D:\proj\AppLoggerNet\AppLogger\bin\Debug\netstandard2.0\AppLogger.dll
  Successfully created package 'D:\proj\AppLoggerNet\AppLogger\bin\Debug\AppLogger.1.0.0.nupkg'.
```

## <a name="publish-the-package"></a><span data-ttu-id="2a8fd-126">パッケージを公開する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-126">Publish the package</span></span>

<span data-ttu-id="2a8fd-127">`.nupkg` ファイルを作成したら、`dotnet nuget push` コマンドと、nuget.org から取得した API キーを使用して、そのファイルを nuget.org に公開します。</span><span class="sxs-lookup"><span data-stu-id="2a8fd-127">Once you have a `.nupkg` file, you publish it to nuget.org using the `dotnet nuget push` command along with an API key acquired from nuget.org.</span></span>

[!INCLUDE[publish-notes](includes/publish-notes.md)]

### <a name="acquire-your-api-key"></a><span data-ttu-id="2a8fd-128">API キーを取得する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-128">Acquire your API key</span></span>

[!INCLUDE[publish-api-key](includes/publish-api-key.md)]

### <a name="publish-with-dotnet-nuget-push"></a><span data-ttu-id="2a8fd-129">dotnet nuget push を使用して公開する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-129">Publish with dotnet nuget push</span></span>

[!INCLUDE[publish-dotnet](includes/publish-dotnet.md)]

### <a name="publish-errors"></a><span data-ttu-id="2a8fd-130">公開エラー</span><span class="sxs-lookup"><span data-stu-id="2a8fd-130">Publish errors</span></span>

[!INCLUDE[publish-errors](includes/publish-errors.md)]


### <a name="manage-the-published-package"></a><span data-ttu-id="2a8fd-131">公開済みパッケージを管理する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-131">Manage the published package</span></span>

[!INCLUDE[publish-manage](includes/publish-manage.md)]

## <a name="related-topics"></a><span data-ttu-id="2a8fd-132">関連トピック</span><span class="sxs-lookup"><span data-stu-id="2a8fd-132">Related topics</span></span>

- [<span data-ttu-id="2a8fd-133">パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="2a8fd-133">Create a Package</span></span>](../create-packages/creating-a-package.md)
- [<span data-ttu-id="2a8fd-134">パッケージの公開</span><span class="sxs-lookup"><span data-stu-id="2a8fd-134">Publish a Package</span></span>](../create-packages/publish-a-package.md)
- [<span data-ttu-id="2a8fd-135">複数のターゲット フレームワークのサポート</span><span class="sxs-lookup"><span data-stu-id="2a8fd-135">Support multiple target frameworks</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="2a8fd-136">パッケージのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="2a8fd-136">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="2a8fd-137">ローカライズされたパッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="2a8fd-137">Creating localized packages</span></span>](../create-packages/creating-localized-packages.md)