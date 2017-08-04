---
title: "[ODBC ソース エディター] ([接続マネージャー] ページ) |Microsoft ドキュメント"
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
- sql13.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 93923df833452025772dd0dbf1df2e17a1582fed
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-source-editor-connection-manager-page"></a>[ODBC ソース エディター] ([接続マネージャー] ページ)
  **[ODBC 入力元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、入力元の ODBC 接続マネージャーを選択できます。 さらにこのページを使用して、データベースのテーブルやビューを選択できます。  
  
 ODBC 入力元の詳細については、「 [ODBC Source](../../integration-services/data-flow/odbc-source.md)」を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[ODBC 入力元エディター] の [接続マネージャー] ページを開くには**  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   **[データ フロー]** タブで、ODBC 入力元をダブルクリックします。  
  
## <a name="options"></a>オプション  
  
### <a name="connection-manager"></a>[ODBC 入力元エディター]  
 既存の ODBC 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。 ODBC でサポートされているデータベースへの接続を選択または入力できます。  
  
### <a name="new"></a>新規  
 **[新規作成]**をクリックします。 新しい ODBC 接続マネージャーを作成できる **[ODBC 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。  
  
### <a name="data-access-mode"></a>[データ アクセス モード]  
 入力元のデータを選択する方法を選択します。 次の表に示すオプションがあります。  
  
|オプション|Description|  
|------------|-----------------|  
|テーブル名|ODBC データ ソースのテーブルまたはビューからデータを取得します。 このオプションを選択する場合は、以下の一覧から値を選択します。|  
||**[テーブル名またはビュー名]**: 使用できるテーブルまたはビューを一覧から選択するか、正規表現を入力してテーブルを特定します。|  
||この一覧には、最初の 1,000 個のテーブルのみが含まれます。 データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (*) を使用すると、目的のテーブルが表示されます。|  
|[SQL コマンド]|SQL クエリを使用して、ODBC データ ソースからデータを取得します。 使用しているソース データベースの構文でクエリを記述してください。 このオプションを選択する場合は、以下のいずれかの方法でクエリを入力します。|  
||**[SQL コマンド テキスト]** フィールドに SQL クエリのテキストを入力します。|  
||**[参照]** をクリックして、テキスト ファイルから SQL クエリを読み込みます。|  
||**[クエリの解析]** をクリックして、クエリ テキストの構文を検証します。|  
  
### <a name="preview"></a>プレビュー  
 **[プレビュー]** をクリックすると、選択したテーブルまたはビューから抽出されたデータを先頭から最大で 200 行表示できます。  
  
## <a name="see-also"></a>参照  
 [ODBC 入力元のカスタム プロパティ](../../integration-services/data-flow/odbc-source-custom-properties.md)   
 [Odbc 入力元エディター & #40 です。[列] ページ &#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)   
 [[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  
