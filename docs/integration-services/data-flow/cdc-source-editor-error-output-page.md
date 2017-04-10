---
title: "[CDC ソース エディター] ([エラー出力] ページ) | Microsoft Docs"
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
  - "sql13.ssis.designer.cdcsource.errorhandling.f1"
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# [CDC ソース エディター] ([エラー出力] ページ)
  **[CDC ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 CDC ソースの詳細については、「 [CDC Source](../../integration-services/data-flow/cdc-source.md)」を参照してください。  
  
## タスク一覧  
 **[CDC ソース エディター] の [エラー出力] ページを開くには**  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、CDC ソースをダブルクリックします。  
  
3.  **[CDC ソース エディター]** で、**[エラー出力]** をクリックします。  
  
## オプション  
 **[入力または出力]**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (ソース) 列を表示します。  
  
 **[エラー]**  
 CDC ソースでフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **切り捨て**  
 CDC ソースでフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **Description**  
 使用されていません。  
  
 **[選択したセルに設定する値]**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを CDC ソースでどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **[適用]**  
 選択したセルにエラー処理オプションを適用します。  
  
## エラー処理オプション  
 CDC ソースでのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
 **エラー コンポーネント**  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
 **エラーを無視する**  
 エラーまたは切り捨ては無視され、データ行は CDC ソース出力に送られます。  
  
 **[フローのリダイレクト]**  
 エラーまたは切り捨てのデータ行は、CDC ソースのエラー出力に送られます。 この場合は、CDC ソースのエラー処理が使用されます。 詳細については、「[CDC ソース](../../integration-services/data-flow/cdc-source.md)」を参照してください。  
  
## 参照  
 [[CDC ソース エディター] &#40;[接続マネージャー] ページ&#41;](../Topic/CDC%20Source%20Editor%20\(Connection%20Manager%20Page\).md)   
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../Topic/CDC%20Source%20Editor%20\(Columns%20Page\).md)  
  
  