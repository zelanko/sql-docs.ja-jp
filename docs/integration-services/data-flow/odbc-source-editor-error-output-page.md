---
title: "[ODBC ソース エディター] ([エラー出力] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.odbcsource.errorhandling.f1"
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# [ODBC ソース エディター] ([エラー出力] ページ)
  **[ODBC 入力元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 ODBC 入力元について詳しくは、「[CDC ソース](../../integration-services/data-flow/cdc-source.md)」をご覧ください。  
  
## タスク一覧  
 **[ODBC 入力元エディター] の [エラー出力] ページを開くには**  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   **[データ フロー]** タブで、ODBC 入力元をダブルクリックします。  
  
-   **[ODBC 入力元エディター]** で、**[エラー出力]** をクリックします。  
  
## オプション  
  
### [入力または出力]  
 データ ソースの名前を表示します。  
  
### 列  
 使用されていません。  
  
### [エラー]  
 ODBC 入力元でフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### 切り捨て  
 ODBC 入力元でフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### Description  
 使用されていません。  
  
### [選択したセルに設定する値]  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを ODBC 入力元でどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### [適用]  
 選択したセルにエラー処理オプションを適用します。  
  
## エラー処理オプション  
 ODBC 入力元でのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
### エラー コンポーネント  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
### エラーを無視する  
 エラーまたは切り捨ては無視されます。  
  
### [フローのリダイレクト]  
 エラーまたは切り捨てが ODBC 入力元のエラー出力に送られる原因となった行。 詳しくは、「[ODBC 入力元](../../integration-services/data-flow/odbc-source.md)」をご覧ください。  
  
## 参照  
 [[ODBC ソース エディター] &#40;[接続マネージャー] ページ&#41;](../Topic/ODBC%20Source%20Editor%20\(Connection%20Manager%20Page\).md)   
 [[ODBC ソース エディター] &#40;[列] ページ&#41;](../Topic/ODBC%20Source%20Editor%20\(Columns%20Page\).md)  
  
  