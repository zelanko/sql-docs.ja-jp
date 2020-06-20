---
title: '[CDC ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 54d61b7696f00aeacdd92a3803630838f6f3ad1a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84923983"
---
# <a name="cdc-source-editor-error-output-page"></a>[CDC ソース エディター] ([エラー出力] ページ)
  **[CDC ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 CDC ソースの詳細については、「 [CDC Source](data-flow/cdc-source.md)」を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[CDC ソース エディター] の [エラー出力] ページを開くには**  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、CDC ソースをダブルクリックします。  
  
3.  **[CDC ソース エディター]** で、 **[エラー出力]** をクリックします。  
  
## <a name="options"></a>オプション  
 **[入力または出力]**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[CDC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (ソース) 列を表示します。  
  
 **Error**  
 CDC ソースでフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **切り捨て**  
 CDC ソースでフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 **説明**  
 使用されていません。  
  
 **[選択したセルに設定する値]**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを CDC ソースでどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
 適用****  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="error-handling-options"></a>エラー処理オプション  
 CDC ソースでのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
 **エラー コンポーネント**  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
 **エラーを無視する**  
 エラーまたは切り捨ては無視され、データ行は CDC ソース出力に送られます。  
  
 **[フローのリダイレクト]**  
 エラーまたは切り捨てのデータ行は、CDC ソースのエラー出力に送られます。 この場合は、CDC ソースのエラー処理が使用されます。 詳細については、「 [CDC ソース](data-flow/cdc-source.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [[CDC ソースエディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [[CDC ソース エディター] &#40;[列] ページ&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
