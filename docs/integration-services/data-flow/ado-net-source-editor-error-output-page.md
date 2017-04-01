---
title: "[ADO NET 変換元エディター] ([エラー出力] ページ) | Microsoft Docs"
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
  - "sql13.dts.designer.adonetsource.erroroutput.f1"
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# [ADO NET 変換元エディター] ([エラー出力] ページ)
  **[ADO NET 変換元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。  
  
 ADO NET 変換元の詳細については、「 [ADO NET Source](../../integration-services/data-flow/ado-net-source.md)」を参照してください。  
  
 **[エラー出力] ページを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。  
  
3.  **[ADO NET 変換元エディター]** で、**[エラー出力]** をクリックします。  
  
## オプション  
 **[入力または出力]**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (変換元) 列を表示します。  
  
 **[エラー]**  
 エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **関連項目:** [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **切り捨て**  
 切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。  
  
 **Description**  
 エラーの説明を表示します。  
  
 **[選択したセルに設定する値]**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **[適用]**  
 選択したセルにエラー処理オプションを適用します。  
  
## 参照  
 [[ADO NET 変換元エディター] ([接続マネージャー] ページ)](../Topic/ADO%20NET%20Source%20Editor%20\(Connection%20Manager%20Page\).md)   
 [[ADO NET 変換元エディター] ([列] ページ)](../Topic/ADO%20NET%20Source%20Editor%20\(Columns%20Page\).md)   
 [ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  