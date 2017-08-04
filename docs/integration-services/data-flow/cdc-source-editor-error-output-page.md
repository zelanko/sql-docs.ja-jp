---
title: "CDC ソース エディター (エラー出力 ページ) |Microsoft ドキュメント"
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
- sql13.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 15818f42922d7fe21bdba64d0bf4c5e4a593eada
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="cdc-source-editor-error-output-page"></a>[CDC ソース エディター] ([エラー出力] ページ)
  **[CDC ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 CDC ソースの詳細については、「 [CDC Source](../../integration-services/data-flow/cdc-source.md)」を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **CDC ソース エディター エラー出力 ページを開く**  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、CDC ソースをダブルクリックします。  
  
3.  **[CDC ソース エディター]**で、 **[エラー出力]**をクリックします。  
  
## <a name="options"></a>オプション  
 **入力/出力**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (ソース) 列を表示します。  
  
 **エラー**  
 CDC ソースでフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **切り捨て**  
 CDC ソースでフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **Description**  
 使用されていません。  
  
 **この値を選択したセルに設定します。**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを CDC ソースでどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **適用**  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="error-handling-options"></a>エラー処理オプション  
 CDC ソースでのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
 **コンポーネントを失敗させる**  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
 **エラーを無視します。**  
 エラーまたは切り捨ては無視され、データ行は CDC ソース出力に送られます。  
  
 **フローのリダイレクト**  
 エラーまたは切り捨てのデータ行は、CDC ソースのエラー出力に送られます。 この場合は、CDC ソースのエラー処理が使用されます。 詳細については、「 [CDC ソース](../../integration-services/data-flow/cdc-source.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC ソース エディター &#40;[接続マネージャー] ページ&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../../integration-services/data-flow/cdc-source-editor-columns-page.md)  
  
  
