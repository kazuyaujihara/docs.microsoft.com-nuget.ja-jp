---
title: "NuGet とは何か。またどのような働きをするのか | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/26/2017
ms.topic: hero-article
ms.prod: nuget
ms.technology: 
ms.assetid: c3faf278-4cbf-4733-96f6-9ee9f7203af9
description: "NuGet とは何で、どのような働きをするのかについて、総合的に紹介します"
keywords: "NuGet パッケージ マネージャー, 消費量, パッケージの作成, パッケージのホスト"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 2bc6a9e154df287fee6a7e00cc1349dfa2100643
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="an-introduction-to-nuget"></a><span data-ttu-id="27241-105">NuGet の概要</span><span class="sxs-lookup"><span data-stu-id="27241-105">An introduction to NuGet</span></span>

<span data-ttu-id="27241-106">最新の開発プラットフォームに欠かせないツールは、開発者が役に立つコードを作成、共有、および使用するために利用できるメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="27241-106">An essential tool for any modern development platform is a mechanism through which developers can create, share, and consume useful  code.</span></span> <span data-ttu-id="27241-107">多くの場合、このようなコードは "パッケージ" にバンドルされています。このパッケージにはコンパイルされたコード (DLL) に加えて、このパッケージが使用されるプロジェクトで必要なその他のコンテンツが含まれています。</span><span class="sxs-lookup"><span data-stu-id="27241-107">Often such code is bundled into a "packages" that contain compiled code (as DLLs) along with other content needed in the projects that consume these packages.</span></span>

<span data-ttu-id="27241-108">.NET のコード共有メカニズムである **NuGet** では、.NET 用のパッケージを作成、ホスト、使用する方法が定義されており、それらの各ロール用のツールが提供されています。</span><span class="sxs-lookup"><span data-stu-id="27241-108">For .NET, the mechanism for sharing code is **NuGet**, which defines how packages for .NET are created, hosted, and consumed, and provides the tools for each of those roles.</span></span> 

<span data-ttu-id="27241-109">つまり、NuGet パッケージは、拡張子が `.nupkg` の 1 つの ZIP ファイルであり、コンパイル済みのコード (DLL)、そのコードに関連する他のファイル、パッケージのバージョン番号などの情報が記述されているマニフェストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="27241-109">Put simply, a NuGet package is a single ZIP file with the `.nupkg` extension that contains compiled code (DLLs), other files related to that code, and a descriptive manifest that includes information like the package's version number.</span></span> <span data-ttu-id="27241-110">ライブラリ開発者は、パッケージ ファイルを作成して、ホストに公開します。</span><span class="sxs-lookup"><span data-stu-id="27241-110">Library developers create package files and publish them to a host.</span></span> <span data-ttu-id="27241-111">パッケージ利用者は、これらのパッケージを受け取り、プロジェクトに追加した後、プロジェクトのコードでライブラリの機能を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="27241-111">Package consumers receive those packages, add them to their projects, and then call that library's functionality in their project code.</span></span> <span data-ttu-id="27241-112">その過程での細部はすべて NuGet 自体が処理します。</span><span class="sxs-lookup"><span data-stu-id="27241-112">NuGet itself then handles all of the intermediate details.</span></span>

## <a name="the-flow-of-packages-between-creators-hosts-and-consumers"></a><span data-ttu-id="27241-113">作成者、ホスト、利用者の間のパッケージのフロー</span><span class="sxs-lookup"><span data-stu-id="27241-113">The flow of packages between creators, hosts, and consumers</span></span>

<span data-ttu-id="27241-114">ホストとしての役割の NuGet は、一般公開されている 60,000 以上の個別パッケージを、[nuget.org](https://www.nuget.org) の中央リポジトリで保持します。これらのパッケージを、毎日数百万人の .NET 開発者が使用しています。</span><span class="sxs-lookup"><span data-stu-id="27241-114">In its role as host, NuGet itself maintains the central repository of over 60,000 unique, publicly-available packages at [nuget.org](https://www.nuget.org). These packages are employed by millions of .NET developers every day.</span></span> <span data-ttu-id="27241-115">また、NuGet を使うと、クラウド、プライベート ネットワーク、さらにはローカル ファイル システムで、プライベートにパッケージをホストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="27241-115">NuGet also enables you to host packages privately in the cloud, on a private network, or even on just your local file system.</span></span> <span data-ttu-id="27241-116">これにより、これらのパッケージは特定の組織や顧客グループ内の開発者だけが利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="27241-116">By doing so, those packages are available to only those developers within a particular organization or customer group.</span></span> <span data-ttu-id="27241-117">オプションの説明については、「[Hosting your own NuGet feeds](Hosting-Packages/Overview.md)」(独自の NuGet フィードのホスト) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27241-117">The options are explained on [Hosting your own NuGet feeds](Hosting-Packages/Overview.md).</span></span>

<span data-ttu-id="27241-118">ホストは、それがどのような性質のであっても、パッケージの "*作成者*" と "*利用者*" の間の接続ポイントとして機能します。</span><span class="sxs-lookup"><span data-stu-id="27241-118">Whatever its nature, a host serves as a point of connection between package *creators* and package *consumers*.</span></span> <span data-ttu-id="27241-119">作成者は、便利な NuGet パッケージを作成して、ホストに公開します。</span><span class="sxs-lookup"><span data-stu-id="27241-119">Creators build useful NuGet packages and publish them to a host.</span></span> <span data-ttu-id="27241-120">利用者は、アクセスできるホストで役に立ち互換性のあるパッケージを検索し、ダウンロードしてプロジェクトに組み込みます。</span><span class="sxs-lookup"><span data-stu-id="27241-120">Consumers then search for useful and compatible packages on accessible hosts, downloading and including those packages in their projects.</span></span> <span data-ttu-id="27241-121">プロジェクトにインストールされたパッケージの API は、プロジェクト コードの他の部分から利用できます。</span><span class="sxs-lookup"><span data-stu-id="27241-121">Once installed in a project, the packages' APIs are available to the rest of the project code.</span></span>

![パッケージ作成者、パッケージ ホスト、パッケージ利用者の間の関係](media/nuget-roles.png)

<span data-ttu-id="27241-123">この場合の "互換性のある" パッケージとは、パッケージを使用するプロジェクトのターゲット フレームワークと互換性のある少なくとも 1 つの .NET Framework 用にビルドされたアセンブリが含まれていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="27241-123">A "compatible" package in this case means that it contains assemblies built for at least one target .NET framework that's compatible with the consuming project's target framework.</span></span> <span data-ttu-id="27241-124">広範な互換性を持つパッケージにするには、作成者は、さまざまなターゲット フレームワーク用に個別のアセンブリをコンパイルし、そのすべてを同じパッケージに収めます。</span><span class="sxs-lookup"><span data-stu-id="27241-124">To make a package widely compatible, its creator compiles separate assemblies for various target frameworks and includes all of them in the same package.</span></span> <span data-ttu-id="27241-125">利用者がそのパッケージをインストールすると、NuGet はプロジェクトで必要なアセンブリだけを抽出します。</span><span class="sxs-lookup"><span data-stu-id="27241-125">When a consumer installs that package, NuGet extracts only those assemblies that are needed by the project.</span></span> <span data-ttu-id="27241-126">これにより、最終的なアプリケーションやそのプロジェクトによって生成されるアセンブリでのパッケージのフットプリントが最小になります。</span><span class="sxs-lookup"><span data-stu-id="27241-126">This minimizes the package's footprint in the final application and/or assemblies produced by that project.</span></span>

## <a name="nuget-tools"></a><span data-ttu-id="27241-127">NuGet のツール</span><span class="sxs-lookup"><span data-stu-id="27241-127">NuGet tools</span></span>

<span data-ttu-id="27241-128">ホストのサポートに加えて、NuGet では作成者と利用者の両方が使用できるさまざまなツールも提供されています。</span><span class="sxs-lookup"><span data-stu-id="27241-128">In addition to hosting support, NuGet also provides a variety of tools used by both creators and consumers:</span></span>

| <span data-ttu-id="27241-129">ツール</span><span class="sxs-lookup"><span data-stu-id="27241-129">Tool</span></span> | <span data-ttu-id="27241-130">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="27241-130">Platforms</span></span> | <span data-ttu-id="27241-131">該当シナリオ</span><span class="sxs-lookup"><span data-stu-id="27241-131">Applicable Scenarios</span></span> | <span data-ttu-id="27241-132">説明</span><span class="sxs-lookup"><span data-stu-id="27241-132">Description</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="27241-133">nuget.exe CLI</span><span class="sxs-lookup"><span data-stu-id="27241-133">nuget.exe CLI</span></span>](Tools/nuget-exe-CLI-Reference.md) | <span data-ttu-id="27241-134">すべて</span><span class="sxs-lookup"><span data-stu-id="27241-134">All</span></span> | <span data-ttu-id="27241-135">作成、利用</span><span class="sxs-lookup"><span data-stu-id="27241-135">Creation, Consumption</span></span> | <span data-ttu-id="27241-136">NuGet のすべての機能を提供します。パッケージ作成者のみに適用されるコマンド、利用者のみに適用されるもの、両方に適用されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="27241-136">Provides all NuGet capabilities, with some commands applying specifically to package creators, some applying only to consumers, and others applying to both.</span></span> <span data-ttu-id="27241-137">たとえば、`nuget pack` コマンドはパッケージ作成者がさまざまなアセンブリと関連ファイルからパッケージを作成するために使い、`nuget install` はパッケージ利用者がプロジェクトにパッケージを組み込むために使い、`nuget config` は全ユーザーが NuGet 構成の変数を設定するために使います。</span><span class="sxs-lookup"><span data-stu-id="27241-137">For example, package creators use the `nuget pack` command to create a package from various assemblies and related files, package consumers use `nuget install` to include packages in a project, and everyone uses `nuget config` to set NuGet configuration variables.</span></span>  |
| [<span data-ttu-id="27241-138">パッケージ マネージャー UI</span><span class="sxs-lookup"><span data-stu-id="27241-138">Package Manager UI</span></span>](Tools/Package-Manager-UI.md) | <span data-ttu-id="27241-139">Windows の Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27241-139">Visual Studio on Windows</span></span> | <span data-ttu-id="27241-140">利用</span><span class="sxs-lookup"><span data-stu-id="27241-140">Consumption</span></span> | <span data-ttu-id="27241-141">.NET プロジェクトでパッケージをインストールして管理するための使いやすい UI を提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-141">Provides an easy-to-use UI for installing and managing packages in .NET projects.</span></span> | 
| [<span data-ttu-id="27241-142">NuGet 管理 UI</span><span class="sxs-lookup"><span data-stu-id="27241-142">Manage NuGet UI</span></span>](/visualstudio/mac/nuget-walkthrough) | <span data-ttu-id="27241-143">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="27241-143">Visual Studio for Mac</span></span> | <span data-ttu-id="27241-144">利用</span><span class="sxs-lookup"><span data-stu-id="27241-144">Consumption</span></span> | <span data-ttu-id="27241-145">.NET プロジェクトでパッケージをインストールして管理するための使いやすい UI を提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-145">Provide an easy-to-use UI for installing and managing packages in .NET projects.</span></span> |
| [<span data-ttu-id="27241-146">パッケージ マネージャー コンソール</span><span class="sxs-lookup"><span data-stu-id="27241-146">Package Manager Console</span></span>](Tools/Package-Manager-Console.md) | <span data-ttu-id="27241-147">Windows の Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27241-147">Visual Studio on Windows</span></span> | <span data-ttu-id="27241-148">利用</span><span class="sxs-lookup"><span data-stu-id="27241-148">Consumption</span></span> | <span data-ttu-id="27241-149">.NET プロジェクトでパッケージをインストールして管理するための [PowerShell コマンド](Tools/Powershell-Reference.md)を提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-149">Provides [PowerShell commands](Tools/Powershell-Reference.md) for installing and managing packages in .NET projects.</span></span> | 
| [<span data-ttu-id="27241-150">dotnet CLI</span><span class="sxs-lookup"><span data-stu-id="27241-150">dotnet CLI</span></span>](Tools/dotnet-Commands.md) | <span data-ttu-id="27241-151">すべて</span><span class="sxs-lookup"><span data-stu-id="27241-151">All</span></span> | <span data-ttu-id="27241-152">作成、利用</span><span class="sxs-lookup"><span data-stu-id="27241-152">Creation, Consumption</span></span> | <span data-ttu-id="27241-153">.NET Core ツール チェーン内で直接、特定の NuGet CLI 機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-153">Provides certain NuGet CLI capabilities directly within the .NET Core toolchain.</span></span> |
| [<span data-ttu-id="27241-154">MSBuild</span><span class="sxs-lookup"><span data-stu-id="27241-154">MSBuild</span></span>](Schema/msbuild-targets.md) | <span data-ttu-id="27241-155">Windows</span><span class="sxs-lookup"><span data-stu-id="27241-155">Windows</span></span> | <span data-ttu-id="27241-156">作成、利用</span><span class="sxs-lookup"><span data-stu-id="27241-156">Creation, Consumption</span></span> | <span data-ttu-id="27241-157">パッケージを作成し、MSBuild ツールチェーンを介してプロジェクトで使われたパッケージを直接復元できます。</span><span class="sxs-lookup"><span data-stu-id="27241-157">Provides the ability to create packages and restore packages used in a project directly through the MSBuild toolchain.</span></span> |

<span data-ttu-id="27241-158">このように、NuGet のどのツールを使うかは、パッケージを作成 (および発行) しているのか、それとも利用しているのかということと、使っているプラットフォームに、大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="27241-158">As you can see, the tools with which you work with NuGet depend greatly on whether you're creating (and publishing) packages or consuming them, and the platform you're working on.</span></span> <span data-ttu-id="27241-159">詳しくは、「[Package creation workflow](Create-Packages/Overview-and-Workflow.md)」(パッケージ作成のワークフロー) と「[Package consumption workflow](Consume-Packages/Overview-and-Workflow.md)」(パッケージ利用のワークフロー) およびこれらのセクションの他のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27241-159">More specific details can be found in the [Package creation workflow](Create-Packages/Overview-and-Workflow.md) and [Package consumption workflow](Consume-Packages/Overview-and-Workflow.md) topics, along with other topics in those sections.</span></span> 

<span data-ttu-id="27241-160">パッケージ作成者は、通常、他の NuGet パッケージの機能を基にして開発を行うので、利用者でもあります。</span><span class="sxs-lookup"><span data-stu-id="27241-160">Package creators are typically also consumers, as they build on top of functionality that exists in other NuGet packages.</span></span> <span data-ttu-id="27241-161">そして、これらのパッケージは、もちろん、他のパッケージにさらに依存している場合があります。</span><span class="sxs-lookup"><span data-stu-id="27241-161">And those packages, of course, may in turn depend on still others.</span></span>

## <a name="managing-dependencies"></a><span data-ttu-id="27241-162">依存関係の管理</span><span class="sxs-lookup"><span data-stu-id="27241-162">Managing dependencies</span></span>

<span data-ttu-id="27241-163">他の開発者の作業を簡単に利用できることは、パッケージ管理システムを非常に強力なものにしている機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="27241-163">The ability to easily build on the work of others is one of the things that makes a package management system so powerful.</span></span> <span data-ttu-id="27241-164">したがって、NuGet の機能の多くは、プロジェクトに代わって依存関係ツリーつまり "グラフ" を管理することです。</span><span class="sxs-lookup"><span data-stu-id="27241-164">Accordingly, much of what NuGet does is managing that dependency tree or "graph" on behalf of your project.</span></span> <span data-ttu-id="27241-165">簡単に言えば、開発者が関心を持つ必要があるのは、プロジェクト内で直接使っているパッケージだけです。</span><span class="sxs-lookup"><span data-stu-id="27241-165">Simply said, you need only concern yourself with those packages that you're directly using in a project.</span></span> <span data-ttu-id="27241-166">そのようなパッケージ自体のいずれかで他のパッケージ (それがさらにパッケージを利用していることがあります) が利用されている場合、ダウンレベルの依存関係はすべて NuGet が処理します。</span><span class="sxs-lookup"><span data-stu-id="27241-166">If any of those packages themselves consume other packages (which can consume packages), NuGet takes care of all those down-level dependencies.</span></span>

<span data-ttu-id="27241-167">次の図で示すプロジェクトは、5 つのパッケージに依存しており、それらがさらに他の複数のパッケージに依存しています。</span><span class="sxs-lookup"><span data-stu-id="27241-167">The following image shows a project that depends on five packages, which in turn depend on a number of others.</span></span>  

![.NET プロジェクトの NuGet 依存関係グラフの例](media/dependency-graph.png)

<span data-ttu-id="27241-169">依存関係グラフの複数の箇所に出現しているパッケージがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="27241-169">Notice that some packages appear multiple times in the dependency graph.</span></span> <span data-ttu-id="27241-170">たとえば、パッケージ B には 3 つの異なるコンシューマーがあり、各コンシューマーがそのパッケージの異なるバージョンを指定している可能性もあります (図には示されていません)。</span><span class="sxs-lookup"><span data-stu-id="27241-170">For example, there are three different consumers of package B, and each consumer might also specify a different version for that package (not shown).</span></span> <span data-ttu-id="27241-171">これはよくあることなので、すべてのコンシューマーの要求を満たすパッケージ B のバージョンを正確に特定する困難な作業はすべて、NuGet が行ってくれます。</span><span class="sxs-lookup"><span data-stu-id="27241-171">Because this is a common occurrence, NuGet fortunately does all the hard work to determine exactly which version of package B satisfies all its consumers.</span></span> <span data-ttu-id="27241-172">その後、NuGet は、依存関係グラフの深さに関係なく、他のすべてのパッケージについても同じように処理します。</span><span class="sxs-lookup"><span data-stu-id="27241-172">NuGet then does the same for all other packages, no matter how deep the dependency graph becomes.</span></span>

<span data-ttu-id="27241-173">NuGet がこのサービスを実行する方法について詳しくは、[依存関係の解決](Consume-Packages/Dependency-Resolution.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27241-173">For more details on how NuGet performs this service, see [Dependency resolution](Consume-Packages/Dependency-Resolution.md).</span></span>

## <a name="tracking-references-and-restoring-packages"></a><span data-ttu-id="27241-174">参照の追跡とパッケージの復元</span><span class="sxs-lookup"><span data-stu-id="27241-174">Tracking references and restoring packages</span></span>

<span data-ttu-id="27241-175">プロジェクトは開発者のコンピューター、ソース管理リポジトリ、ビルド サーバーなどの間を簡単に移動するので、プロジェクトに直接バインドされた NuGet パッケージからバイナリ アセンブリを維持するのは極めて困難です。</span><span class="sxs-lookup"><span data-stu-id="27241-175">Because projects can easily move between developer computers, source control repositories, build servers, and so forth, it's highly impractical to keep binary assemblies from NuGet packages directly bound to a project.</span></span> <span data-ttu-id="27241-176">プロジェクトの各コピーが必要以上に肥大化する (それにより、ソース管理リポジトリ内の領域を浪費する) だけでなく、パッケージのバイナリを新しいバージョンに更新する処理も、プロジェクトの全コピーについて行う必要があるため、非常に困難になります。</span><span class="sxs-lookup"><span data-stu-id="27241-176">Not only would this make each copy of the project unnecessarily bloated (and thereby waste space in source control repositories), it would also make it very difficult to update package binaries to newer versions as this would have to be done across all copies of the project.</span></span> 

<span data-ttu-id="27241-177">代わりに、NuGet は、単にプロジェクトが依存するパッケージの参照リストを保持し (最上位と下位レベルの依存関係を含みます)、要求に応じて参照されているすべてのパッケージを復元する手段を提供します (「[パッケージ復元](Consume-Packages/Package-Restore.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="27241-177">Instead, NuGet simply maintains a reference list of the packages upon which a project depends (including both top-level and down-level dependencies), and provides the means to restore all referenced packages upon request as described on [Package restore](Consume-Packages/Package-Restore.md).</span></span> <span data-ttu-id="27241-178">つまり、どこかのホストからプロジェクトにパッケージをインストールすると常に、NuGet によってパッケージの ID とバージョン番号がこの参照リストに記録されます </span><span class="sxs-lookup"><span data-stu-id="27241-178">That is, whenever you install a package from some host into a project, NuGet records the package identifier and version number in this reference list.</span></span> <span data-ttu-id="27241-179">(もちろん、パッケージをアンインストールするとリストから削除されます)。</span><span class="sxs-lookup"><span data-stu-id="27241-179">(Uninstalling a package, of course, removes it from the list.)</span></span> 

![NuGet の参照リストはパッケージのインストール時に作成され、別の場所にパッケージを復元するために使うことができる](media/nuget-restore.png)

<span data-ttu-id="27241-181">それ以降いつでも、NuGet は、参照リストのみを使って、パブリック ホストやプライベート ホストからすべてのパッケージを再インストール、つまり復元できます。</span><span class="sxs-lookup"><span data-stu-id="27241-181">With only the reference list, NuGet can then reinstall&mdash;that is, restore&mdash;all of those packages from public and/or private hosts at any later time.</span></span> <span data-ttu-id="27241-182">このため、nuget.org では、公開されたパッケージを非公開にすることはできますが、完全に削除することはできません (「[Deleting packages](Policies/deleting-packages.md)」(パッケージの削除) を参照)。ソース管理にプロジェクトをコミットするとき、またはプロジェクトを他のなんらかの方法で共有するときは、参照リストを含めるだけでよく、パッケージのバイナリを含める必要はありません (「[パッケージとソース管理](Consume-Packages/Packages-and-Source-Control.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="27241-182">(For this reason, nuget.org does not allow permanent deletion of published packages, although they can be hidden; see [Deleting packages](Policies/deleting-packages.md).) When committing a project to source control, or sharing it in some other way, you need only include the reference list and need not include any package binaries (see [Packages and source control](Consume-Packages/Packages-and-Source-Control.md).)</span></span>

<span data-ttu-id="27241-183">自動展開システムの一部としてプロジェクトのコピーを取得するビルド サーバーのような、プロジェクトを受け取るコンピューターは、必要なときに依存関係を復元するよう NuGet に要求するだけです。</span><span class="sxs-lookup"><span data-stu-id="27241-183">The computer that receives a project, such as a build server obtaining a copy of the project as part of an automated deployment system, simply asks NuGet to restore dependencies whenever they're needed.</span></span> <span data-ttu-id="27241-184">Visual Studio Team Services などのビルド システムでは、この目的のための "NuGet 復元" ステップが提供されています。</span><span class="sxs-lookup"><span data-stu-id="27241-184">Build systems like Visual Studio Team Services provide "NuGet restore" steps for this exact purpose.</span></span> <span data-ttu-id="27241-185">同様に、開発者がプロジェクトのコピーを取得するときは (リポジトリを複製するときと同じように)、Visual Studio でプロジェクトを開いてビルドを実行すると、Visual Studio が自動的に必要な NuGet パッケージを復元します。</span><span class="sxs-lookup"><span data-stu-id="27241-185">Similarly, when developers obtain a copy of a project (as when cloning a repository) then open the project in Visual Studio and run a build, Visual Studio automatically restores the necessary NuGet packages.</span></span> <span data-ttu-id="27241-186">開発者は、パッケージ マネージャー コンソールで `nuget restore` CLI コマンドまたは`Install-Package` コマンドレットを使って、いつでも NuGet にパッケージの復元を指示できます。</span><span class="sxs-lookup"><span data-stu-id="27241-186">Developers can also tell NuGet to restore packages at any time using the `nuget restore` CLI command or the `Install-Package` cmdlet in the Package Manager Console.</span></span>

<span data-ttu-id="27241-187">その場合に開発者が関係する NuGet の主要な役割は明らかに、プロジェクトに代わってその参照リストを維持し、参照されているパッケージを効率的に復元 (および更新) する手段を提供することです。</span><span class="sxs-lookup"><span data-stu-id="27241-187">Clearly, then, NuGet's primary role where developers are concerned is maintaining that reference list on behalf of your project and providing the means to efficiently restore (and update) those referenced packages.</span></span>

<span data-ttu-id="27241-188">その方法は NuGet のバージョンと共に変化しているため、次のように複数の "*パッケージ管理形式*" が存在します。</span><span class="sxs-lookup"><span data-stu-id="27241-188">How this exactly happens has evolved over the different versions of NuGet, resulting in several *package management formats*, as they're called:</span></span>

- <span data-ttu-id="27241-189">[`packages.config`](Schema/packages-config.md): *(NuGet 1.0 以降)* プロジェクト内のすべての依存関係のフラット リストを保持する XML ファイルです。インストールされている他のパッケージの依存関係も含みます。</span><span class="sxs-lookup"><span data-stu-id="27241-189">[`packages.config`](Schema/packages-config.md): *(NuGet 1.0+)* An XML file that maintains a flat list of all dependencies in the project, including the dependencies of other installed packages.</span></span> 
- <span data-ttu-id="27241-190">[`project.json`](Schema/project-json.md): *(NuGet 3.0 以降)* プロジェクトの依存関係のリストを保持する JSON ファイルです。全体的なパッケージ グラフは関連するファイル `project.lock.json` に含まれます。</span><span class="sxs-lookup"><span data-stu-id="27241-190">[`project.json`](Schema/project-json.md): *(NuGet 3.0+)* A JSON file that maintains a list of the project's dependencies with an overall package graph in an associated file, `project.lock.json`.</span></span> <span data-ttu-id="27241-191">この構造は `packages.config` よりパフォーマンスがよく (「[NuGet でのパッケージ依存関係の解決方法](Consume-Packages/Dependency-Resolution.md)」を参照)、推移的な復元を含みますが、一般に以下の PackageReference に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="27241-191">This structure provides improved performance over `packages.config` as described on [Dependency Resolution](Consume-Packages/Dependency-Resolution.md), including transitive restore, but has itself been generally superseded by PackageReference below.</span></span>
- <span data-ttu-id="27241-192">[プロジェクト ファイルでのパッケージ参照](Consume-Packages/Package-References-in-Project-Files.md) ("PackageReference" とも呼ばれます) | *(NuGet 4.0 以降)* プロジェクトの最上位レベルの依存関係のリストがプロジェクト ファイル内に直接保持されるので、別のファイルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="27241-192">[Package references in project files](Consume-Packages/Package-References-in-Project-Files.md) (also known as "PackageReference") | *(NuGet 4.0+)* Maintains a list of a project's top-level dependencies directly within the project file, so no separate file is needed.</span></span> <span data-ttu-id="27241-193">関連するファイル `project.assets.json` は、全体的な依存関係グラフを管理するために `project.lock.json` のように動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="27241-193">An associated file, `project.assets.json`, is dynamically generated like `project.lock.json` to manage the overall dependency graph.</span></span>

<span data-ttu-id="27241-194">指定されたプロジェクトでどのパッケージ管理形式が採用されるかは、プロジェクトの種類と、NuGet および Visual Studio の使用可能なバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="27241-194">Which package management format is employed in any given project depends on the project type, and the available version of NuGet and Visual Studio.</span></span> <span data-ttu-id="27241-195">使われている形式を確認するには、最初のパッケージをインストールした後で、プロジェクトのルートにある `packages.config` または `project.json` を調べます。</span><span class="sxs-lookup"><span data-stu-id="27241-195">To check what format is being used, simply look for `packages.config` or `project.json` in the project root after installing your first package.</span></span> <span data-ttu-id="27241-196">どちらのファイルも見つからない場合は、プロジェクト ファイルで直接 &lt;PackageReference&gt; 要素を調べます。</span><span class="sxs-lookup"><span data-stu-id="27241-196">If you don't see either file, look in the project file directly for a &lt;PackageReference&gt;element.</span></span>

<span data-ttu-id="27241-197">たとえば、Visual Studio 2017 では、プロジェクトのほとんどの種類は `packages.config` を使います (UWP C# と .NET Core プロジェクトだけは PackageReference を使います)。</span><span class="sxs-lookup"><span data-stu-id="27241-197">In Visual Studio 2017, for example, most project types use `packages.config` except for UWP C# and .NET Core projects which use PackageReference.</span></span> 

## <a name="what-else-does-nuget-do"></a><span data-ttu-id="27241-198">NuGet の他の機能</span><span class="sxs-lookup"><span data-stu-id="27241-198">What else does NuGet do?</span></span>

<span data-ttu-id="27241-199">これまで説明した内容をまとめると、NuGet は (ホスティングの役割では) 集中リポジトリ nuget.org を提供し、プライベート ホスティングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="27241-199">To summarize what we've covered so far, NuGet provides (in its hosting role) the central nuget.org repository and supports private hosting.</span></span> <span data-ttu-id="27241-200">NuGet は、開発者がパッケージの作成、公開、使用に必要なツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-200">NuGet provides the tools developers need for creating, publishing, and consuming packages.</span></span> <span data-ttu-id="27241-201">そして最も重要なことは、NuGet はプロジェクトで使われているパッケージの参照リストを保持し、そのリストからパッケージを更新および復元する機能を提供するということです。</span><span class="sxs-lookup"><span data-stu-id="27241-201">And most importantly, NuGet maintains a reference list of packages used in a project and the ability to restore and update those packages from that list.</span></span>

<span data-ttu-id="27241-202">これらの処理を効率的に実行するため、NuGet はバックグラウンドでいくつかの最適化を行います。</span><span class="sxs-lookup"><span data-stu-id="27241-202">To make these processes work efficiently, NuGet does some behind-the-scenes optimizations.</span></span> <span data-ttu-id="27241-203">最も顕著なのは、NuGet がコンピューター全体とプロジェクト固有両方のパッケージ キャッシュを管理して、インストールと再インストールを短縮することです。</span><span class="sxs-lookup"><span data-stu-id="27241-203">Most notably, NuGet manages both computer-wide and project-specific package caches to shortcut installation and reinstallation.</span></span> <span data-ttu-id="27241-204">コンピューター全体のキャッシュに関しては、プロジェクトでダウンロードしてインストールしたすべてのパッケージはキャッシュに格納されるので、同じパッケージを別のプロジェクトでインストールするときに再度ダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="27241-204">Where the computer-wide cache is concerned, any package that you download and install in a project is stored in the cache, such that installing the same package in another project doesn't have to download it again.</span></span> <span data-ttu-id="27241-205">これは、ビルド サーバーなどのように多数のパッケージを頻繁に復元する場合は明らかに非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="27241-205">This is clearly very helpful when you're frequently restoring a larger number of packages, as on a build server.</span></span> <span data-ttu-id="27241-206">そのメカニズムと使い方について詳しくは、「[NuGet のキャッシュを管理する](Consume-Packages/Managing-the-Nuget-Cache.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27241-206">For more details on the mechanism and how to work with it, see [Managing the NuGet cache](Consume-Packages/Managing-the-Nuget-Cache.md).</span></span>

<span data-ttu-id="27241-207">個々のプロジェクトでは、NuGet は依存関係グラフ全体を管理するために多くの作業を行います </span><span class="sxs-lookup"><span data-stu-id="27241-207">Within an individual project, NuGet does a lot of work to manage the overall dependency graph.</span></span> <span data-ttu-id="27241-208">(`project.json` または &lt;PackageReference&gt; を使うときは、NuGet はそれぞれの情報を `project.lock.json` および `project.assets.json` という名前のセカンダリ ファイルに保持します)。これにはやはり、同じパッケージの異なるバージョンへの複数の参照の解決が含まれます。</span><span class="sxs-lookup"><span data-stu-id="27241-208">(When using `project.json` or &lt;PackageReference&gt;, NuGet keeps that information in a secondary file called `project.lock.json` and `project.assets.json`, respectively.) This again includes resolving multiple references to different versions of the same package.</span></span>

<span data-ttu-id="27241-209">つまり、プロジェクトが 1 つ以上のパッケージに依存関係を持ち、それらのパッケージ自体にも同じような依存関係があることは、ごく一般的なことです。</span><span class="sxs-lookup"><span data-stu-id="27241-209">That is, it's quite common that a project takes a dependency on one or more packages that themselves have the same dependencies.</span></span> <span data-ttu-id="27241-210">たとえば、nuget.org の最も便利なユーティリティ パッケージのいくつかは、他の多くのパッケージで使われています。</span><span class="sxs-lookup"><span data-stu-id="27241-210">For example, some of the most useful utility packages on nuget.org are employed by many other packages.</span></span> <span data-ttu-id="27241-211">依存関係グラフ全体では、同じパッケージの異なるバージョンに対する 10 個の異なる参照が簡単にできてしまいます。</span><span class="sxs-lookup"><span data-stu-id="27241-211">In the entire dependency graph, ten, you could easily have ten different references to different versions of the same package.</span></span> <span data-ttu-id="27241-212">しかし、そのパッケージの複数のバージョンをアプリケーション自体に組み込みたくはないので、NuGet は誰でも使うことができる 1 つのバージョンを選別します </span><span class="sxs-lookup"><span data-stu-id="27241-212">However, you don't want to bring multiple versions of that package into the application itself, so NuGet sorts out which single version that everyone can use.</span></span> <span data-ttu-id="27241-213">(詳しくは、このトピックの「[NuGet でのパッケージ依存関係の解決方法](Consume-Packages/Dependency-Resolution.md)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="27241-213">(See [Dependency Resolution](Consume-Packages/Dependency-Resolution.md) for more on this topic.)</span></span>

<span data-ttu-id="27241-214">さらに、NuGet は、パッケージの構成方法 ([ローカライズ](Create-Packages/Creating-Localized-Packages.md)と[デバッグ シンボル](Create-Packages/Symbol-Packages.md)を含みます) およびパッケージの参照方法 ([バージョン参照](reference/package-versioning.md#version-ranges-and-wildcards)と[プレリリース バージョン](create-packages/Prerelease-Packages.md)を含みます) に関するすべての仕様を保持しています。NuGet は、資格情報プロバイダー用の API (プライベート ホストへのアクセス用) および Visual Studio 拡張機能とプロジェクト テンプレートを作成する開発者用の API も提供します。</span><span class="sxs-lookup"><span data-stu-id="27241-214">Beyond that, NuGet maintains all the specifications related to how packages are structured (including [localization](Create-Packages/Creating-Localized-Packages.md) and [debug symbols](Create-Packages/Symbol-Packages.md)) and how they are referenced (including [version ranges](reference/package-versioning.md#version-ranges-and-wildcards) and [pre-release versions](create-packages/Prerelease-Packages.md).) NuGet also provides APIs for credential providers (for accessing private hosts) and for developers who write Visual Studio extensions and project templates.</span></span>

<span data-ttu-id="27241-215">このドキュメントの目次を見るとわかるように、これらすべての機能に関するトピックと、最初の NuGet からのすべてのリリース ノートが提供されています。</span><span class="sxs-lookup"><span data-stu-id="27241-215">Take a moment to browse the table of contents for this documentation, and you'll see all of these capabilities represented there, along with release notes dating back to NuGet's beginnings.</span></span>

## <a name="comments-contributions-and-issues"></a><span data-ttu-id="27241-216">コメント、投稿、問題</span><span class="sxs-lookup"><span data-stu-id="27241-216">Comments, contributions, and issues</span></span>

<span data-ttu-id="27241-217">最後に、このドキュメントに関するコメントや投稿をお寄せください。各ページの **[コメント]** および **[編集]** コマンドを使うか、GitHub の[ドキュメント リポジトリ](https://github.com/NuGet/docs.microsoft.com-nuget/)および[ドキュメント問題リスト](https://github.com/NuGet/docs.microsoft.com-nuget/issues)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="27241-217">Finally, we very much welcome comments and contributions to this documentation&mdash;just select the **Comments** and **Edit** commands on any page, or visit the [docs repository](https://github.com/NuGet/docs.microsoft.com-nuget/) and [docs issue list](https://github.com/NuGet/docs.microsoft.com-nuget/issues) on GitHub.</span></span>

<span data-ttu-id="27241-218">また、[さまざまな GitHub リポジトリ](https://github.com/NuGet/Home)から NuGet 自体への投稿も歓迎します。NuGet の問題については、[https://github.com/NuGet/home/issues](https://github.com/NuGet/home/issues) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27241-218">We also welcome contributions to NuGet itself through its [various GitHub repositories](https://github.com/NuGet/Home); NuGet issues can be found on [https://github.com/NuGet/home/issues](https://github.com/NuGet/home/issues).</span></span>

<span data-ttu-id="27241-219">NuGet のエクスペリエンスをお楽しみください。</span><span class="sxs-lookup"><span data-stu-id="27241-219">Enjoy your NuGet experience!</span></span>