<span data-ttu-id="0161f-101">`push` コマンドのエラーは、通常、問題があることを示します。</span><span class="sxs-lookup"><span data-stu-id="0161f-101">Errors from the `push` command typically indicate the problem.</span></span> <span data-ttu-id="0161f-102">たとえば、プロジェクトのバージョン番号の更新を忘れて、既に存在するパッケージを公開しようとした場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="0161f-102">For example, you may have forgotten to update the version number in your project and are therefore trying to publish a package that already exists.</span></span>

<span data-ttu-id="0161f-103">また、ホストに既に存在する識別子を使用してパッケージを公開しようとするとエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0161f-103">You also see errors when trying to publish a package using an identifier that already exists on the host.</span></span> <span data-ttu-id="0161f-104">たとえば、"AppLogger" という名前は既に存在します。</span><span class="sxs-lookup"><span data-stu-id="0161f-104">The name "AppLogger", for example, already exists.</span></span> <span data-ttu-id="0161f-105">その場合、`push` コマンドを実行すると、次のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0161f-105">In such a case, the `push` command gives the following error:</span></span>

```output
Response status code does not indicate success: 403 (The specified API key is invalid,
has expired, or does not have permission to access the specified package.).
```

<span data-ttu-id="0161f-106">作成したばかりの有効な API キーを使用している場合、エラーの "アクセス許可" 部分では完全には明白ではありませんが、このメッセージは名前の競合を示します。</span><span class="sxs-lookup"><span data-stu-id="0161f-106">If you're using a valid API key that you just created, then this message indicates a naming conflict, which isn't entirely clear from the "permission" part of the error.</span></span> <span data-ttu-id="0161f-107">パッケージ識別子を変更し、プロジェクトをリビルドして、 `.nupkg` ファイルを再作成した後、`push` コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="0161f-107">Change the package identifier, rebuild the project, recreate the `.nupkg` file, and retry the `push` command.</span></span>