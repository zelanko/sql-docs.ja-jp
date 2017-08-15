---
title: "[ADO NET ソース エディター]\\ ([接続マネージャー] ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a76ec3875ab02de069e6feef699aff302d4dc5fd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="ado-net-source-editor-connection-manager-page"></a>[ADO NET 変換元エディター]\ ([接続マネージャー] ページ)
  **[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換元の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを選択できます。 さらにこのページを使用して、データベースのテーブルやビューを選択できます。  
  
 ADO NET 変換元の詳細については、「 [ADO NET Source](../../integration-services/data-flow/ado-net-source.md)」を参照してください。  
  
 **接続マネージャー ページを開きます**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。  
  
3.  **[ADO NET 変換元エディター]**で、 **[接続マネージャー]**をクリックします。  
  
## <a name="static-options"></a>静的オプション  
 **ADO.NET 接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]**をクリックして新しい接続を作成します。  
  
 **新機能**  
 **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。  
  
 **データ アクセス モード**  
 ソースからデータを選択する方法を指定します。  
  
|オプション|Description|  
|------------|-----------------|  
|[テーブルまたはビュー]|[!INCLUDE[vstecado](../../includes/vstecado-md.md)] データ ソースのテーブルまたはビューからデータを取得します。|  
|[SQL コマンド]|SQL クエリを使用して、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データ ソースからデータを取得します。|  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー** では、最大で 200 行を表示できます。  
  
> [!NOTE]  
>  データをプレビューするときに、CLR ユーザー定義型を含む列にはデータが表示されません。 代わりに、値\<値が大きすぎるため表示 > または System.byte[] として表示します。 前者は、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーを使用してデータ ソースにアクセスする場合に表示されます。後者は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダーを使用している場合に表示されます。  
  
## <a name="data-access-mode-dynamic-options"></a>データ アクセス モードの動的オプション  
  
### <a name="data-access-mode--table-or-view"></a>[データ アクセス モード] = [テーブルまたはビュー]  
 **テーブルまたはビューの名前**  
 データ ソースで使用できるテーブルまたはビューの一覧から、テーブルまたはビューの名前を選択します。  
  
### <a name="data-access-mode--sql-command"></a>[データ アクセス モード] = [SQL コマンド]  
 **SQL コマンド テキスト**  
 SQL クエリのテキストを入力し、 **[クエリの作成]**をクリックしてクエリを作成するか、 **[参照]**をクリックしてクエリ テキストを含むファイルを指定します。  
  
 **クエリを作成します。**  
 SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。  
  
 **[参照]**  
 **[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。  
  
## <a name="see-also"></a>参照  
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [[ADO NET 変換元エディター] &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/ado-net-source-editor-error-output-page.md)   
 [ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  
