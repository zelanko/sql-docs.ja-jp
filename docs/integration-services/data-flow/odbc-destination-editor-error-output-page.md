---
title: "ODBC 変換先エディター ([エラー出力] ページ) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcdest.errorhandling.f1"
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# ODBC 変換先エディター ([エラー出力] ページ)
  **[ODBC 入力先エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 ODBC 入力先の詳細については、「 [ODBC Destination](../../integration-services/data-flow/odbc-destination.md)」を参照してください。  
  
 **[ODBC 入力先エディター] の [エラー出力] ページを開くには**  
  
## タスク一覧  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、ODBC 入力先を含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   **[データ フロー]** タブで、ODBC 入力先をダブルクリックします。  
  
-   **[ODBC 入力先エディター]**で、 **[エラー出力]**をクリックします。  
  
## オプション  
  
### [入力または出力]  
 データ ソースの名前を表示します。  
  
### 列  
 使用されていません。  
  
### [エラー]  
 ODBC 入力先でフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### 切り捨て  
 ODBC 入力先でフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### Description  
 エラーの説明を表示します。  
  
### [選択したセルに設定する値]  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを ODBC 入力先でどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### [適用]  
 選択したセルにエラー処理オプションを適用します。  
  
## エラー処理オプション  
 ODBC 入力先でのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
### エラー コンポーネント  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
### エラーを無視する  
 エラーまたは切り捨ては無視されます。  
  
### [フローのリダイレクト]  
 エラーまたは切り捨てが ODBC 入力先のエラー出力に送られる原因となった行。 詳細については、「ODBC 入力先」を参照してください。  
  
## 参照  
 [ODBC 変換先エディター ([接続マネージャー] ページ)](../Topic/ODBC%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [ODBC 変換先エディター ([マッピング] ページ)](../Topic/ODBC%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
  