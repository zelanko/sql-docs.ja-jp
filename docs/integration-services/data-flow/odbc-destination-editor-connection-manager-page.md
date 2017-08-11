---
title: "ODBC 変換先エディター (接続マネージャー ページ) |Microsoft ドキュメント"
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
- sql13.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0f2e090b24ea11734f758033f7137523c9f2036b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-destination-editor-connection-manager-page"></a>[ODBC 変換先エディター] ([接続マネージャー] ページ)
  **[ODBC 入力先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、入力先の ODBC 接続マネージャーを選択できます。 さらにこのページを使用して、データベースのテーブルやビューを選択できます。  
  
 ODBC 入力先の詳細については、「 [ODBC Destination](../../integration-services/data-flow/odbc-destination.md)」を参照してください。  
  
 **[ODBC 入力先エディター] の [接続マネージャー] ページを開くには**  
  
## <a name="task-list"></a>タスク一覧  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、ODBC 入力先を含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   **[データ フロー]** タブで、ODBC 入力先をダブルクリックします。  
  
-   **[ODBC 入力先エディター]**で、 **[接続マネージャー]**をクリックします。  
  
## <a name="options"></a>オプション  
  
### <a name="connection-manager"></a>[ODBC 入力先エディター]  
 既存の ODBC 接続マネージャーを一覧から選択するか、[新規作成] をクリックして新しい接続を作成します。 ODBC でサポートされているデータベースへの接続を選択または入力できます。  
  
### <a name="new"></a>新規  
 **[新規作成]**をクリックします。 新しい接続マネージャーを作成できる **[ODBC 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。  
  
### <a name="data-access-mode"></a>[データ アクセス モード]  
 データを入力先に読み込む方法を選択します。 次の表に示すオプションがあります。  
  
|オプション|Description|  
|------------|-----------------|  
|[テーブル名 - バッチ]|バッチ モードで動作する ODBC 入力先を構成するには、このオプションを選択します。 このオプションを選択した場合は、次のオプションを指定できます。|  
||**[テーブル名またはビュー名]**: 使用できるテーブルまたはビューを一覧から選択します。<br /><br /> この一覧には、最初の 1,000 個のテーブルのみが含まれます。 データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。<br /><br /> **[バッチ サイズ]**: 一括読み込みのバッチのサイズを入力します。 これは、バッチとして読み込まれる行数です。|  
|[テーブル名 - 行ごと]|一度に 1 行ずつ、入力先テーブルに各行を挿入するように ODBC 入力先を構成するには、このオプションを選択します。 このオプションを選択した場合は、次のオプションを指定できます。|  
||**[テーブル名またはビュー名]**: 使用できるテーブルまたはビューを一覧のデータベースから選択します。<br /><br /> この一覧には、最初の 1,000 個のテーブルのみが含まれます。 データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (*) を使用すると、目的のテーブルが表示されます。|  
  
### <a name="preview"></a>プレビュー  
 **[プレビュー]** をクリックすると、選択したテーブルのデータが最大で 200 行表示されます。  
  
## <a name="see-also"></a>参照  
 [ODBC 入力先のカスタム プロパティ](../../integration-services/data-flow/odbc-destination-custom-properties.md)   
 [[ODBC 変換先エディター] &#40;[マッピング] ページ&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [ODBC 変換先エディター &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/odbc-destination-editor-error-output-page.md)  
  
  
