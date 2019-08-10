---
ms.openlocfilehash: e8949e9964ed19d342df53f08f59bb0f89e5feb0
ms.sourcegitcommit: 5aa49478dc466c67db5c3edda7c6ce8dcd8ae033
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817485"
---
<span data-ttu-id="a97b4-101">パッケージ識別子とバージョン番号は、パッケージに含まれる正確なコードを一意に識別するため、プロジェクトの中で最も重要な 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="a97b4-101">The package identifier and the version number are the two most important values in the project because they uniquely identify the exact code that's contained in the package.</span></span>

<span data-ttu-id="a97b4-102">**パッケージ識別子のベスト プラクティス:**</span><span class="sxs-lookup"><span data-stu-id="a97b4-102">**Best practices for the package identifier:**</span></span>

- <span data-ttu-id="a97b4-103">**一意性**:この識別子は、nuget.org 全体で、あるいはパッケージをホストするギャラリー全体で一意になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a97b4-103">**Uniqueness**: The identifier must be unique across nuget.org or whatever gallery hosts the package.</span></span> <span data-ttu-id="a97b4-104">識別子を決める前に、該当するギャラリーを検索し、その名前が既に使用されていないか確認してください。</span><span class="sxs-lookup"><span data-stu-id="a97b4-104">Before deciding on an identifier, search the applicable gallery to check if the name is already in use.</span></span> <span data-ttu-id="a97b4-105">競合を避けるために、`Contoso.` のように、識別子の最初の部分に会社の名前を使用することが適しているパターンです。</span><span class="sxs-lookup"><span data-stu-id="a97b4-105">To avoid conflicts, a good pattern is to use your company name as the first part of the identifier, such as `Contoso.`.</span></span>
- <span data-ttu-id="a97b4-106">**名前空間のような名前**:.NET の名前空間に似たパターンに従います。ハイフンの代わりにドット表記を使います。</span><span class="sxs-lookup"><span data-stu-id="a97b4-106">**Namespace-like names**: Follow a pattern similar to namespaces in .NET, using dot notation instead of hyphens.</span></span> <span data-ttu-id="a97b4-107">たとえば、`Contoso-Utility-UsefulStuff` や `Contoso_Utility_UsefulStuff` ではなく `Contoso.Utility.UsefulStuff` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a97b4-107">For example, use `Contoso.Utility.UsefulStuff` rather than `Contoso-Utility-UsefulStuff` or `Contoso_Utility_UsefulStuff`.</span></span> <span data-ttu-id="a97b4-108">パッケージ識別子がコードで使用される名前空間と一致すれば、利用者にとっても便利です。</span><span class="sxs-lookup"><span data-stu-id="a97b4-108">Consumers also find it helpful when the package identifier matches the namespaces used in the code.</span></span>
- <span data-ttu-id="a97b4-109">**サンプル パッケージ**:別のパッケージの使用方法を示すサンプル コードのパッケージを生成する場合、`Contoso.Utility.UsefulStuff.Sample` のように、識別子にサフィックスとして `.Sample` を付けます。</span><span class="sxs-lookup"><span data-stu-id="a97b4-109">**Sample Packages**: If you produce a package of sample code that demonstrates how to use another package, attach `.Sample` as a suffix to the identifier, as in `Contoso.Utility.UsefulStuff.Sample`.</span></span> <span data-ttu-id="a97b4-110">(サンプル パッケージは、もちろん、他のパッケージに依存します。)サンプル パッケージを作成する場合は、`<IncludeAssets>` 内で `contentFiles` 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="a97b4-110">(The sample package would of course have a dependency on the other package.) When creating a sample package, use the `contentFiles` value in `<IncludeAssets>`.</span></span> <span data-ttu-id="a97b4-111">`content` フォルダーで、`\Samples\Contoso.Utility.UsefulStuff.Sample` のように、`\Samples\<identifier>` という名前のフォルダーにサンプル コードを配置します。</span><span class="sxs-lookup"><span data-stu-id="a97b4-111">In the `content` folder, arrange the sample code in a folder called `\Samples\<identifier>` as in `\Samples\Contoso.Utility.UsefulStuff.Sample`.</span></span>

<span data-ttu-id="a97b4-112">**パッケージ バージョンのベスト プラクティス:**</span><span class="sxs-lookup"><span data-stu-id="a97b4-112">**Best practices for the package version:**</span></span>

- <span data-ttu-id="a97b4-113">これは厳密には必須ではありませんが、一般的にはプロジェクト (またはアセンブリ) と一致するようにパッケージのバージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="a97b4-113">In general, set the version of the package to match the project (or assembly), though this is not strictly required.</span></span> <span data-ttu-id="a97b4-114">パッケージを単一のアセンブリに限定する場合に、これはシンプルな方法です。</span><span class="sxs-lookup"><span data-stu-id="a97b4-114">This is a simple matter when you limit a package to a single assembly.</span></span> <span data-ttu-id="a97b4-115">概して、NuGet 自体は依存関係の解決時、パッケージ バージョンを使います。アセンブリ バージョンではありません。</span><span class="sxs-lookup"><span data-stu-id="a97b4-115">Overall, remember that NuGet itself deals with package versions when resolving dependencies, not assembly versions.</span></span>
- <span data-ttu-id="a97b4-116">非標準のバージョン スキーマを使用するとき、「[パッケージのバージョン管理](../../reference/package-versioning.md)」で説明するように、NuGet バージョン管理ルールを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a97b4-116">When using a non-standard version scheme, be sure to consider the NuGet versioning rules as explained in [Package versioning](../../reference/package-versioning.md).</span></span> <span data-ttu-id="a97b4-117">NuGet は、ほぼ [semver 2 に準拠](../../reference/package-versioning.md#semantic-versioning-200)しています。</span><span class="sxs-lookup"><span data-stu-id="a97b4-117">NuGet is mostly [semver 2 compliant](../../reference/package-versioning.md#semantic-versioning-200).</span></span>

> <span data-ttu-id="a97b4-118">依存関係の解決については、「[PackageReference による依存関係の解決](../../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a97b4-118">For information on dependency resolution, see [Dependency resolution with PackageReference](../../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference).</span></span> <span data-ttu-id="a97b4-119">バージョン管理の理解を深めるためにも役立つ可能性がある旧情報については、こちらの一連のブログ投稿を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a97b4-119">For older information that may also be helpful to better understand versioning, see this series of blog posts.</span></span>
>
> - [<span data-ttu-id="a97b4-120">第 1 部: DLL 地獄</span><span class="sxs-lookup"><span data-stu-id="a97b4-120">Part 1: Taking on DLL Hell</span></span>](http://blog.davidebbo.com/2011/01/nuget-versioning-part-1-taking-on-dll.html)
> - [<span data-ttu-id="a97b4-121">第 2 部: コア アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="a97b4-121">Part 2: The core algorithm</span></span>](http://blog.davidebbo.com/2011/01/nuget-versioning-part-2-core-algorithm.html)
> - [<span data-ttu-id="a97b4-122">第 3 部:バインド リダイレクトによる統合</span><span class="sxs-lookup"><span data-stu-id="a97b4-122">Part 3: Unification via Binding Redirects</span></span>](http://blog.davidebbo.com/2011/01/nuget-versioning-part-3-unification-via.html)