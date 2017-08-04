---
title: "ADO NET 変換元エディター ([エラー出力] ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7889b092dae9abe613b3c4b2fe8d18500dea69f0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="ado-net-source-editor-error-output-page"></a>[ADO NET 変換元エディター] ([エラー出力] ページ)
  **[ADO NET 変換元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。  
  
 ADO NET 変換元の詳細については、「 [ADO NET Source](../../integration-services/data-flow/ado-net-source.md)」を参照してください。  
  
 **エラー出力 ページを開きます**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。  
  
3.  **[ADO NET 変換元エディター]**で、 **[エラー出力]**をクリックします。  
  
## <a name="options"></a>オプション  
 **入力/出力**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (変換元) 列を表示します。  
  
 **エラー**  
 エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **関連項目:** [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **切り捨て**  
 切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。  
  
 **Description**  
 エラーの説明を表示します。  
  
 **この値を選択したセルに設定します。**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **適用**  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="see-also"></a>参照  
 [[ADO NET 変換元エディター] &#40;[接続マネージャー] ページ&#41;](../../integration-services/data-flow/ado-net-source-editor-connection-manager-page.md)   
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  
