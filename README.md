# The JFK Files
> Explore the JFK Assassination files using the AI Enrichment features of Azure Cognitive Search. You can watch the demo in action in a short [online video](https://channel9.msdn.com/Shows/AI-Show/Using-Cognitive-Search-to-Understand-the-JFK-Documents) or explore the JFK files yourself with our [online demo](https://aka.ms/jfkfiles-demo).

Azure Cognitive SearchのAI Enrichment機能を使って、JFK暗殺事件のファイルを探索します。短い[オンラインビデオ](https://channel9.msdn.com/Shows/AI-Show/Using-Cognitive-Search-to-Understand-the-JFK-Documents)でデモの動作をご覧いただくか、[オンラインデモ](https://aka.ms/jfkfiles-demo)でJFKのファイルをご自身で探索することができます。

## Cognitive Search - An AI-first approach to content understanding
> This project demonstrates how you can use both the built-in and custom AI in Cognitive Search. Cognitive Search ingests your data from almost any datasource and enriches it using a set of cognitive skills that extracts knowledge and then lets you explore the data using Search.

このプロジェクトでは、Cognitive SearchのビルトインAIとカスタムAIの両方をどのように利用できるかをデモします。Cognitive Searchは、ほぼすべてのデータソースからデータを取り込み、知識を抽出する一連の認識スキルを使用してデータを強化し、Searchを使用してデータを探索できるようにします。

![JFK files Cognitive Search](images/jfk-cognitive-search.jpg)

## JFK Files Architecture
> The JFK files example leverages the built-in Cognitive Skills inside of Cognitive Search and combines it with custom skills using extensibility.  The architecture below showcases how the new Cognitive Search capabilities of Azure enable you to easily create structure from almost any datasource.

JFKファイルの例では、Cognitive Searchに内蔵されているCognitive Skillsを活用し、拡張性を利用してカスタムスキルを組み合わせています。 以下のアーキテクチャは、Azure の新しい Cognitive Search 機能によって、ほとんどすべてのデータソースから簡単に構造を作成できることを示すものです。

![Architecture](images/jfk-files-architecture.JPG)

> Note: This diagram of visuals are inspired by the [CIA's JFK document management system in 1997](https://www.archives.gov/files/research/jfk/releases/docid-32404466.pdf) included in the JFK files.

注：このビジュアルの図は、JFKファイルに含まれる[1997年のCIAのJFK文書管理システム](https://www.archives.gov/files/research/jfk/releases/docid-32404466.pdf)から着想を得ています。

> This project includes the following capabilities for you to build your own version of the JFK files.

このプロジェクトには、あなたがJFKファイルの独自のバージョンを構築するための以下の機能が含まれています。

1. > We have provided a subset of the [JFK PDF documents](https://www.archives.gov/research/jfk/2017-release) and images that have been uploaded to the cloud into Azure Blob Storage.
    - クラウドにアップロードされた[JFKのPDF文書](https://www.archives.gov/research/jfk/2017-release)と画像のサブセットをAzure Blob Storageに提供しました。
2. > An [Azure Search](https://azure.microsoft.com/en-us/services/search/) service is used to index the content and power the UX experience. We use the new Cognitive Search capabilities to apply pre-built cognitive skills to the content, and we also use the extensibility mechanism to add custom skills using [Azure Functions](https://azure.microsoft.com/en-us/services/functions/).
    - [Azure Search](https://azure.microsoft.com/ja-jp/services/search/)サービスは、コンテンツのインデックスとUXエクスペリエンスの強化に使用されています。新しいCognitive Searchの機能を使用して、あらかじめ構築されたコグニティブスキルをコンテンツに適用します。また、拡張性メカニズムを使用して、[Azure Functions](https://azure.microsoft.com/ja-jp/services/functions/)を使用してカスタムスキルを追加します。
    1. > Uses the [Cognitive Services Vision API](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/) to extract text information from the image via OCR, and image captioning,
        - [Cognitive Services Vision API](https://azure.microsoft.com/ja-jp/services/cognitive-services/computer-vision/)を使用して、OCRにより画像からテキスト情報を抽出し、画像キャプションを作成します。
    2. > Applies Named Entity Recognitition to extract named entities from the documents,
        - Named Entity Recognititionを適用し、文書から名前付きエンティティを抽出する。
    3. > Annotates text using a custom [CIA Cryptonyms](https://www.maryferrell.org/php/cryptdb.php) skill,
        - [CIA Cryptonyms](https://www.maryferrell.org/php/cryptdb.php)のカスタムスキルを使用してテキストに注釈を付けます。
    4. > Generates [HOCR content](https://en.wikipedia.org/wiki/HOCR) based on results.
        - 結果に基づいて[HOCRコンテンツ](https://en.wikipedia.org/wiki/HOCR)を生成する。
3. > A standalone website to search the index and explore the documents
    - インデックスを検索し、ドキュメントを探索するためのスタンドアローンWebサイト

## Limitations and Considerations
1. > This is a demo to showcase a Cognitive Search use case.  It is not intended to be a framework or scalable architecture for all scenarios, though it can give you an idea of what your scenario might end up looking like.
    - これはコグニティブサーチのユースケースを紹介するためのデモです。 これは、すべてのシナリオのためのフレームワークまたはスケーラブルなアーキテクチャを意図したものではありませんが、あなたのシナリオがどのようなものになるかのアイデアを与えることができます。
2. > The OCR technology is not perfect; results will vary greatly by scan and image quality.
    - OCR技術は完全ではありません。結果はスキャンや画像の品質によって大きく異なります。
3. > Most file formats and datasources are supported, however some scanned and native PDF formats may not be parsed correctly.
    - ほとんどのファイル形式とデータソースに対応していますが、一部のスキャンしたファイルやネイティブのPDF形式は正しく解析されない場合があります。
4. > **IMPORTANT: The JFK Files sample creates a public website and a publicly readable storage container for any extracted images.  As-is, it is not suitable for using with non-public data.**
    - **重要：JFK Filesサンプルは、公開ウェブサイトと、抽出されたすべての画像のための一般に読み取り可能なストレージコンテナを作成します。このままでは、非公開のデータを使用するのには適していません。**

## Setting up your own JFK files library

> These instructions will help you have your own version of the JFK files demo running in Azure in about 20 minutes, with most of that time being provisioning/deployment time.

これらの手順を実行することで、20分程度でAzureでJFKファイルデモの独自バージョンを実行することができます（その時間のほとんどはプロビジョニング/デプロイメント時間です）。

### Prerequisites
1. > An Azure Subscription you can access and deploy resources to.
    - リソースにアクセスし、デプロイすることができるAzureサブスクリプション。
    1. > Note that this demo requires writing to an Azure Storage Account, which you will be billed monthly for the storage written to, and by default provisions a Basic Azure Search service which is billed hourly.  For an estimation of cost, reference the [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/).  In addition, you will be charged for the Cognitive Search part of the demo, which is transaction based.  These charges used with the provided files should be about $15 USD.  [See here for details](https://docs.microsoft.com/en-us/azure/search/cognitive-search-attach-cognitive-services) on what costs may look like if you choose to use Cognitive Search with your own dataset.
        - このデモでは、Azure Storage Account に書き込む必要があり、書き込んだストレージに対して毎月課金されます。また、デフォルトでは、時間単位で課金される Basic Azure Search サービスが提供されます。コストの見積もりについては、[Azure Pricing Calculator](https://azure.microsoft.com/ja-jp/pricing/calculator/) を参照してください。また、デモの Cognitive Search 部分については、トランザクションベースで課金されます。提供されたファイルを使用したこれらの料金は、約15米ドルです。独自のデータセットで Cognitive Search を使用する場合のコストの詳細については、[こちらを参照してください](https://docs.microsoft.com/ja-jp/azure/search/cognitive-search-attach-cognitive-services)。
2. > [Visual Studio 2019](https://www.visualstudio.com/downloads/) with [Azure Developer Tools](https://azure.microsoft.com/en-us/tools/) enabled.  The free community edition will work fine.
    - [Azure Developer Tools](https://azure.microsoft.com/en-us/tools/)を有効にした[Visual Studio 2019](https://www.visualstudio.com/downloads/)。無償のコミュニティ版でも問題なく動作します。
3. > [Node.js](https://nodejs.org/) must be installed on your computer.
    - [Node.js](https://nodejs.org/)がコンピュータにインストールされている必要があります。
4. > Basic familiarity with using the [Azure Portal](https://portal.azure.com) and cloning and compiling code from github.
    - [Azure Portal](https://portal.azure.com)の使用とgithubからのコードのクローンやコンパイルに基本的に慣れていること。

### Deploy Required Resources

1. > Click the below button to upload the provided ARM template to the Azure portal, which is written to automatically deploy and configure the following resources:
    - 以下のボタンをクリックすると、提供された ARM テンプレートが Azure ポータルにアップロードされ、以下のリソースが自動的に配置、設定されるように記述されています。
    1. > An Azure Search service, default set to [Basic](https://azure.microsoft.com/en-us/pricing/details/search/) tier.
        - Azure Search サービスで、デフォルトは [Basic](https://azure.microsoft.com/ja-jp/pricing/details/search/) 階層に設定されています。
    2. > An Azure Blob Storage Account, default set to [Standard LRS](https://azure.microsoft.com/en-us/pricing/details/storage/) tier.
        - Azure Blob Storage アカウント。デフォルトは [Standard LRS](https://azure.microsoft.com/ja-jp/pricing/details/storage/) 階層に設定されています。
    3. > An Azure App Service plan, default set to [Free F1](https://azure.microsoft.com/en-us/pricing/details/app-service/plans/) tier.
        - Azure App Service のプランで、デフォルトは [Free F1](https://azure.microsoft.com/ja-jp/pricing/details/app-service/plans/) tier に設定されています。
    4. > An Azure Web App Service, using the plan from # 3.
        - Azure Web App Service、# 3 のプランを使用します。
    5. > An Azure Function instance, using the storage account from # 2 and the plan from # 3.  The Azure Function will be prepublished with the code provided in this repository as part of the template deployment.
        - 2のストレージアカウントと3のプランを使用したAzure Functionインスタンスです。Azure Functionは、テンプレートのデプロイの一部として、このリポジトリで提供されるコードで事前に公開されます。
    6. > A Cognitive Services account, of type [CognitiveServices](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/), that will be used for billing your Cognitive Search skills usage.
        - Cognitive Searchスキルの使用料を請求するために使用されるCognitive Servicesアカウント（タイプ：[CognitiveServices](https://azure.microsoft.com/ja-jp/pricing/details/cognitive-services/)）です。

    </br>
    <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoft%2FAzureSearch_JFK_Files%2Fmaster%2Fazuredeploy.json" target="_blank">
        <img src="http://azuredeploy.net/deploybutton.png"/>
    </a>

2. > Be sure to select the appropriate subscription to deploy to, and create a new resource group for these resources. Only use alphanumeric lowercase characters for the Resource Prefix field.
    - 必ず、配備先として適切なサブスクリプションを選択し、これらのリソース用に新しいリソースグループを作成してください。Resource Prefixフィールドには、英数字の小文字のみを使用してください。
3. > Review the rest of the parameters as well as the terms and conditions, select the checkbox for "I agree to the terms and conditions stated above", and press "Purchase".
    - 残りのパラメータと利用規約を確認し、「上記の利用規約に同意します」のチェックボックスを選択し、「購入する」を押してください。
4. > Monitor the status of the deployment by following the link that appears in the Azure portal notifications.  It takes about 5 minutes for the resources to be fully provisioned and deployed.
    - Azure ポータルの通知に表示されるリンクをたどって、デプロイの状況を監視してください。リソースが完全にプロビジョニングされ、デプロイされるまでには、約5分かかります。

    ![Deployment in progress](images/deploymentInProgress.JPG)

### Initialize the code

5. > While you are waiting for the resources to finish provisioning, either git clone or download this repo, and open the provided solution file *JfkWebApiSkills/JfkWebApiSkills.sln* using Visual Studio 2019.
    - リソースのプロビジョニングが終了するのを待っている間に、このレポをgit cloneするかダウンロードし、提供されたソリューションファイル*JfkWebApiSkills/JfkWebApiSkills.sln*をVisual Studio 2019で開きます。
6. > In the root of the *JfkInitializer* project, open the *App.config* file.  You will be copying and pasting some secrets into this file momentarily.
    - *JfkInitializer*プロジェクトのルートで、App.configファイルを開いてください。このファイルには、いくつかの秘密をコピーして貼り付けることになります。
7. > Make sure that the *JfkInitializer* project is set as your default project if it isn't already.
    - *JfkInitializer*プロジェクトがデフォルトプロジェクトとして設定されていない場合は、設定されていることを確認します。

### Run the initializer

8. > Once your resources are finished deploying (you should get a notification in the Azure portal), navigate to the *Outputs* section of the deployment.
    - リソースのデプロイが完了したら（Azure ポータルに通知が表示されるはずです）、デプロイの *出力* セクションに移動します。

    ![Deployment completed](images/deploymentCompleted.JPG)

    ![Outputs of deployment](images/outputs.JPG)

9. > Copy and paste each of the provided outputs from this interface into their corresponding value location in the *App.config* file from before.
    - このインターフェースから提供される各出力を、先ほどの*App.config*ファイルの対応する値の場所にコピー＆ペーストしてください。

10. > Save your changes to the *App.config* file, and press the start button at the top of Visual Studio in order to run the initializer.
    - 変更した内容を *App.config* ファイルに保存し、Visual Studio 上部のスタートボタンを押すと、イニシャライザーが実行されます。

    ![Run initializer](images/runInitializer.JPG)

11. > After a few seconds, the message "Website keys have been set.  Please build the website and then return here and press any key to continue." will be output to the console app.  At this point, open a separate cmd window and cd into the directory of where you cloned or downloaded the repo.  Then run the following commands:
    - 数秒後、"Website keys have been set. "というメッセージが表示されます。Please build the website and then return here and press any key to continue." というメッセージがコンソールアプリに出力されます。この時点で、別のcmdウィンドウを開き、レポをクローンまたはダウンロードしたディレクトリにcdしてください。そして、以下のコマンドを実行します。

    ```shell
    cd frontend
    npm install
    npm run build:prod
    ```

12. > After the commands finish running, return to the console app and press any key to continue.
    - コマンドの実行が終了したら、コンソールアプリに戻り、いずれかのキーを押して続行します。

13. > Once the website is deployed, a URL will appear in the console.  Copy and paste this URL into a browser to start interacting with what you have created!
    - ウェブサイトがデプロイされると、コンソールにURLが表示されます。このURLをコピーしてブラウザに貼り付けると、作成したものとやり取りを始めることができます!

    ![URL in console](images/urlInConsole.JPG)

### Results

> This project will create several things for you.  It will deploy an Azure Function using the code provided in the *JfkWebApiSkills* project, as well as create an Azure Search data source, skillset, synonym map, index, and indexer.  It will also create a blob storage container that the images will be reuploaded to, as well as deploys the JFK Files frontend to an Azure web app that you can immediately interact with.  Feel free to play with the code to see how all of these things are accomplished so that you can start using Cognitive Search for your data enrichment scenario today.

このプロジェクトは、あなたに代わっていくつかのものを作成します。*JfkWebApiSkills* プロジェクトで提供されるコードを使用して Azure Function をデプロイし、Azure Search データソース、スキルセット、同義語マップ、インデックス、およびインデクサを作成します。また、画像を再アップロードするための blob ストレージ コンテナを作成し、JFK Files フロントエンドを Azure Web アプリにデプロイして、すぐに対話できるようにします。あなたのデータエンリッチメントのシナリオに今日からCognitive Searchを使用できるように、これらのすべてがどのように達成されるのか、コードを自由に遊んでみてください。

### Debugging

> If you encounter issues running this demo, there are several ways you can debug what may be wrong.

このデモを実行して問題が発生した場合、何が問題なのかをデバッグする方法がいくつかあります。

1. > In *./JfkWebApiSkills/JfkInitializer/Program.cs*, you can set the "DebugMode" variable to true in order to see the output for REST calls that are made to create resources and why they may be failing.  The Initializer will prompt you to do this if it suspects there is an issue creating anything it needs to create.
    - *./JfkWebApiSkills/JfkInitializer/Program.cs* で、変数 "DebugMode" を true に設定すると、リソースを作成するために行われた REST コールの出力とその失敗の原因を確認することができるようになります。イニシャライザーは、作成する必要があるものの作成に問題があると疑われる場合、これを実行するように要求します。
2. > You can add the "enriched" field to your index to see detailed output of all skills that are run.  [Details on how to do this can be found here.](https://docs.microsoft.com/azure/search/cognitive-search-concept-troubleshooting#tip-4-looking-at-enriched-documents-under-the-hood)  You will be making this change in *./JfkWebApiSkills/JfkInitializer/SearchResources.cs*.
    - インデックスに「エンリッチド」フィールドを追加すると、実行されたすべてのスキルの詳細な出力を見ることができます。[この方法の詳細については、こちらをご覧ください](https://docs.microsoft.com/azure/search/cognitive-search-concept-troubleshooting#tip-4-looking-at-enriched-documents-under-the-hood)。この変更は、*./JfkWebApiSkills/JfkInitializer/SearchResources.cs*で行うことになります。
3. > If all else fails, feel free to [post your problem as a Github issue](https://github.com/Microsoft/AzureSearch_JFK_Files/issues/new), which we monitor and respond to when necessary.
    - また、[Githubのissueに投稿していただく](https://github.com/Microsoft/AzureSearch_JFK_Files/issues/new)と、監視して必要なときに対応します。

## Next Steps

> The [Azure Architecture Center](https://aka.ms/architecture) has more content on [this solution](https://docs.microsoft.com/azure/architecture/solution-ideas/articles/cognitive-search-with-skillsets) and others in this space.

[Azure Architecture Center](https://aka.ms/architecture)は、[このソリューション](https://docs.microsoft.com/azure/architecture/solution-ideas/articles/cognitive-search-with-skillsets)とこの分野の他のコンテンツについて、より多くのコンテンツを提供しています。
