---
title: '[ODBC ソースエディター] ([接続マネージャー] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bea70ca9d5d511660ff19a84165a7fc7921b6de1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057218"
---
# <a name="odbc-source-editor-connection-manager-page"></a>[ODBC ソース エディター] ([接続マネージャー] ページ)
  
  **[ODBC 入力元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、入力元の ODBC 接続マネージャーを選択できます。 さらにこのページを使用して、データベースのテーブルやビューを選択できます。  
  
 ODBC 入力元の詳細については、「 [ODBC Source](data-flow/odbc-source.md)」を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[ODBC 入力元エディター] の [接続マネージャー] ページを開くには**  
  
-   
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   
  **[データ フロー]** タブで、ODBC 入力元をダブルクリックします。  
  
## <a name="options"></a>オプション  
  
### <a name="connection-manager"></a>[接続マネージャー]  
 既存の ODBC 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。 ODBC でサポートされているデータベースへの接続を選択または入力できます。  
  
### <a name="new"></a>新規  
 **[新規作成]** をクリックします。 新しい ODBC 接続マネージャーを作成できる **[ODBC 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。  
  
### <a name="data-access-mode"></a>[データ アクセス モード]  
 入力元のデータを選択する方法を選択します。 次の表に示すオプションがあります。  
  
|オプション|[説明]|  
|------------|-----------------|  
|テーブル名|ODBC データ ソースのテーブルまたはビューからデータを取得します。 このオプションを選択する場合は、以下の一覧から値を選択します。|  
||**テーブルまたはビューの名前**: 使用できるテーブルまたはビューを一覧から選択するか、正規表現を入力してテーブルを識別します。|  
||この一覧には、最初の 1,000 個のテーブルのみが含まれます。 データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (*) を使用すると、目的のテーブルが表示されます。|  
|[SQL コマンド]|SQL クエリを使用して、ODBC データ ソースからデータを取得します。 使用しているソース データベースの構文でクエリを記述してください。 このオプションを選択する場合は、以下のいずれかの方法でクエリを入力します。|  
||**[SQL コマンド テキスト]** フィールドに SQL クエリのテキストを入力します。|  
||**[参照]** をクリックして、テキスト ファイルから SQL クエリを読み込みます。|  
||**[クエリの解析]** をクリックして、クエリ テキストの構文を検証します。|  
  
### <a name="preview"></a>プレビュー  
 **[プレビュー]** をクリックすると、選択したテーブルまたはビューから抽出されたデータを先頭から最大で 200 行表示できます。  
  
## <a name="see-also"></a>参照  
 [ODBC 入力元のカスタムプロパティ](data-flow/odbc-source-custom-properties.md)   
 [ODBC ソースエディターの [列の &#40;] ページ&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)   
 [ODBC ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
