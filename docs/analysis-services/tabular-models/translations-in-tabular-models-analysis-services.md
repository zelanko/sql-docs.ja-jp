---
title: "表形式モデル (Analysis Services) での翻訳 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e67f88f5-9f0c-4f19-ab09-558c56ca9335
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 28ff4ea7472597ae86b426ec0a15de399f56d14f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="translations-in-tabular-models-analysis-services"></a>表形式モデルでの翻訳 (Analysis Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]表形式モデルに対する翻訳文字列のサポートを追加します。 モデル内の単一オブジェクトには、名前または説明の複数の翻訳を含めることができます。これにより、モデル定義内で複数の言語バージョンをサポートできるようになります。  
  
 翻訳された文字列は、Excel のピボットテーブル リストなどのクライアント ツールに表示される、オブジェクト メタデータ (テーブルと列の名前と説明) のみに使用されます。  翻訳された文字列を使用するには、クライアント接続でカルチャを指定します。 **Excel で分析** 機能では、ドロップダウン リストから言語を選択することができます。 その他のツールでは、接続文字列にカルチャを指定する必要がある場合があります。  
  
 この機能は、翻訳されたデータをモデルに読み込むことを意図していません。 翻訳されたデータの値を読み込む場合は、文字列を提供するデータ ソースからの翻訳された文字列の抽出を含む、処理の方法を開発する必要があります。  
  
 翻訳済みメタデータを追加するための一般的なワークフローは、次のようになります。  
  
-   文字列の翻訳ごとにプレースホルダーを含む、空の翻訳 JSON ファイルを作成する  
  
-   JSON ファイルに文字列の翻訳を追加する  
  
-   翻訳をモデルにインポートし直す  
  
-   モデルをビルド、処理または配置する  
  
-   接続文字列の LCID を許可するクライアント アプリケーションを使用して、モデルに接続する  
  
## <a name="create-an-empty-translation-file"></a>空の翻訳ファイルの作成  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用して翻訳を追加します。  
  
1.  **[モデル]** > **[翻訳]** > **[翻訳の管理]**の順にクリックします。  
  
2.  翻訳を提供している言語を選択して、 **[追加]**をクリックします。  
  
3.  後で文字列をインポートする方法に応じて、リストから 1 つ以上の言語を選択します。  
  
     翻訳ファイルには複数の言語を含めることができますが、言語ごとに翻訳ファイルを作成すると、より簡単に翻訳を管理できる場合があります。 作成中の翻訳ファイルは、後でその全体にインポートされます。 言語によってインポート オプションを変えるには、各言語を自身のファイルに含める必要があります。  
  
4.  **[言語ファイルのエクスポート]**をクリックします。  ファイル名と場所を指定します。  
  
 ![ssas 表形式-変換-エクスポート](../../analysis-services/tabular-models/media/ssas-tabular-translate-export.png "ssas 表形式の変換のエクスポート")  
  
## <a name="add-translations"></a>翻訳の追加  
 空の JSON 翻訳ファイルには、特定の言語の翻訳に対するメタデータが含まれます。 オブジェクト名と説明の翻訳のプレースホルダーは、モデル定義の最後の **Culture** セクションに指定されます。 次の翻訳を追加することができます。  
  
|||  
|-|-|  
|translatedCaption|表形式モデルの視覚エフェクトをサポートしている任意のクライアント アプリケーションに表示されるテーブルまたは列のタイトル。|  
|translatedDescription|キャプションよりは一般的ではない、SSDT などのモデリング ツールでモデル情報として表示される説明。|  
  
 ファイルから指定されていないメタデータを削除しないでください。  このメタデータは、基となるファイルと一致する必要があります。 必要な文字列を追加して、ファイルを保存します。  
  
 変更が必要なように見える場合がありますが、  **referenceCulture** セクションには、モデルの既定のカルチャのメタデータが含まれています。 **referenceCulture** セクションに加えた変更は、インポート中に読み取られることはありません。これらの変更は無視されます。  
  
 次の例では、 **DimProduct** テーブルと **DimCustomer** テーブルの翻訳されたキャプションと説明を示します。  
  
 ![ssas-テーブル-変換-json](../../analysis-services/tabular-models/media/ssas-tabular-translate-json.png "ssas-テーブル-変換-json")  
  
> [!TIP]  
>  ファイルを開くために JSON エディターを使用できますが、Visual Studio 内で JSON エディターを使用することをお勧めします。ここでは、SSDT で表形式モデルの定義を表示するために、ソリューション エクスプローラーで [コードの表示] コマンドを使用することもできます。 JSON エディターを取得するには、 [通常版の Visual Studio 2015 のインストール](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx)が必要です。 無料の Community Edition には、JSON エディションが含まれます。  
  
## <a name="import-a-translation-file"></a>翻訳ファイルのインポート  
 インポートする翻訳文字列は、モデル定義の一部として恒久的に保存されます。 文字列がインポートされると、翻訳ファイルが参照されなくなります。  
  
1.  **[モデル]** > **[翻訳]** > **[翻訳のインポート]**の順にクリックします。  
  
2.  翻訳ファイルを検索して、 **[開く]**をクリックします。  
  
3.  必要に応じて、インポート オプションを指定します。  
  
    |||  
    |-|-|  
    |既存の翻訳を上書き|インポートされているファイルと同じ言語のすべての既存のキャプションまたは説明を置き換えます。|  
    |無効なオブジェクトを無視|メタデータの不一致を無視するか、またはエラーとしてフラグを設定するかを指定します。|  
    |インポートの結果をログ ファイルに書き込む|ログ ファイルは、既定ではプロジェクト フォルダーに保存されます。 インポートが終了した後に、ファイルの正確なパスが提供されます。 ログ ファイルの名前は、ssdt_translations_log _\<タイムスタンプ >。|  
    |インポートする前に翻訳を JSON ファイルにバックアップする|インポートされている文字列のカルチャに一致する既存の翻訳をバックアップします。  インポートされているカルチャがモデルに存在しない場合は、バックアップは空になります。<br /><br /> 後でこのファイルを復元する必要がある場合は、この JSON ファイルを使用して、model.bim のコンテンツを置き換えることができます。|  
  
4.  **[インポート]**をクリックします。  
  
5.  必要に応じて、ログ ファイルまたはバックアップを作成した場合は、プロジェクト フォルダーでファイルを見つけることができます (例: C:\Users\Documents\Visual Studio 2015\Projects\Tabular1200-AW\Tabular1200-AW)。  
  
6.  インポートを検証するには、次の手順に従います。  
  
    -   ソリューション エクスプローラーで **model.bim** を右クリックして、 **[コードの表示]**を選択します。 **[はい]** をクリックし、デザイン ビューを閉じて、もう一度コード ビューで **model.bim** を開きます。  無料の Community Edition など、通常版の Visual Studio をインストールした場合、ファイルは組み込みの JSON エディターで開きます。  
  
    -   **Culture** または特定の翻訳された文字列を検索して、想定した文字列が実際に存在することを確認します。  
  
## <a name="connect-using-a-locale-identifier"></a>ロケール識別子を使用した接続  
 このセクションでは、正しい文字列がモデルから返されることを検証するための方法について説明します。  
  
1.  Excel で、表形式モデルに接続します。 この手順では、モデルが配置されていると仮定します。 モデルがワークスペースにのみ存在する場合は、モデルを Analysis Services インスタンスに配置して、検証チェックを完了します。  
  
     または、 **Excel で分析** 機能を使用して、モデルに接続することができます  
  
2.  Excel 接続ダイアログ ボックスで、モデルに存在する文字列の翻訳のカルチャを選択します。 Excel では、モデルに定義されているカルチャを検出し、それに応じてドロップダウン リストが設定されます。  
  
     ![ssas の表形式の翻訳-excel](../../analysis-services/tabular-models/media/ssas-tabular-translations-excel.png "ssas-テーブルの翻訳、excel")  
  
     ピボットテーブルを作成するときに、翻訳済みのテーブルおよび列名が表示されます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Excel で分析 (SSAS テーブル)](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  

