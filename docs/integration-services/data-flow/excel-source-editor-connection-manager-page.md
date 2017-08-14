---
title: "[Excel ソース エディター]\\ ([接続マネージャー] ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c1f01be71a5093945a49c43a3a2aec334db7584b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="excel-source-editor-connection-manager-page"></a>[Excel ソース エディター]\ ([接続マネージャー] ページ)
  **[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ノードを使用すると、変換元として [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ブックを選択して使用できます。 Excel ソースは、既存のブックのワークシートまたは名前付き範囲からデータを読み取ります。  
  
> [!NOTE]  
>  Excel ソースの **CommandTimeout** プロパティは **[Excel ソース エディター]**ではアクセスできませんが、 **[詳細エディター]**を使用して設定できます。 このプロパティの詳細については、「 [Excel のカスタム プロパティ](../../integration-services/data-flow/excel-custom-properties.md)」 の Excel ソースのセクションを参照してください。  
  
 Excel ソースの詳細については、「 [Excel Source](../../integration-services/data-flow/excel-source.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **OLE DB 接続マネージャー**  
 既存の Excel 接続マネージャーを一覧から選択するか、 **[新規作成]**をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[Excel 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。  
  
 **[データ アクセス モード]**  
 ソースからデータを選択する方法を指定します。  
  
|値|Description|  
|-----------|-----------------|  
|[テーブルまたはビュー]|Excel ファイルのワークシートまたは名前付き範囲からデータを取得します。|  
|[テーブル名またはビュー名の変数]|ワークシートまたは範囲の名前を変数に指定します。<br /><br /> **関連情報:** [パッケージで変数を使用する](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|[SQL コマンド]|SQL クエリを使用して、Excel ファイルからデータを取得します。 クエリ構文の詳細については、「 [Excel ソース](../../integration-services/data-flow/excel-source.md)」を参照してください。|  
|[変数からの SQL コマンド]|SQL クエリ テキストを変数で指定します。|  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
## <a name="data-access-mode-dynamic-options"></a>データ アクセス モードの動的オプション  
  
### <a name="data-access-mode--table-or-view"></a>[データ アクセス モード] = [テーブルまたはビュー]  
 **[Excel シートの名前]**  
 Excel ブックで使用できるワークシートまたは名前付き範囲の名前を一覧から選択します。  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>[データ アクセス モード] = [テーブル名またはビュー名の変数]  
 **[変数名]**  
 ワークシートまたは名前付き範囲の名前が含まれている変数を選択します。  
  
### <a name="data-access-mode--sql-command"></a>[データ アクセス モード] = [SQL コマンド]  
 **[SQL コマンド テキスト]**  
 SQL クエリのテキストを入力し、 **[クエリの作成]**をクリックしてクエリを作成します。または、 **[参照]**をクリックし、クエリ テキストが含まれているファイルを参照します。  
  
 **パラメーター**  
 クエリ テキスト内でパラメーターのプレースホルダーとして "?" を使用することにより、 パラメーター化クエリを入力した場合は、 **[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、クエリ入力パラメーターをパッケージ変数にマップします。  
  
 **Build query**  
 SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。  
  
 **[参照]**  
 **[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。  
  
 **[クエリの解析]**  
 クエリ テキストの構文を検査します。  
  
### <a name="data-access-mode--sql-command-from-variable"></a>データ アクセス モードが [変数からの SQL コマンド] の場合  
 **[変数名]**  
 SQL クエリのテキストを含む変数を選択します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Excel ソース エディターと &#40; です。「 列」 ページと &#41; です。](../../integration-services/data-flow/excel-source-editor-columns-page.md)   
 [Excel ソース エディターと &#40; です。エラー出力 ページと &#41; です。](../../integration-services/data-flow/excel-source-editor-error-output-page.md)   
 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Excel をループ処理のファイルおよび Foreach ループ コンテナーを使用してテーブル](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
