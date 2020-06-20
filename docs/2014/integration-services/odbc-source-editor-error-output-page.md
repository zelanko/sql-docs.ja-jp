---
title: '[ODBC ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4653b963bd5e8f997832f153a09d87aaeef9c39c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965002"
---
# <a name="odbc-source-editor-error-output-page"></a>[ODBC ソース エディター] ([エラー出力] ページ)
  **[ODBC 入力元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択できます。  
  
 ODBC 入力元について詳しくは、「 [CDC ソース](data-flow/cdc-source.md)」をご覧ください。  
  
## <a name="task-list"></a>タスク一覧  
 **[ODBC 入力元エディター] の [エラー出力] ページを開くには**  
  
-   [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
-   **[データ フロー]** タブで、ODBC 入力元をダブルクリックします。  
  
-   **[ODBC 入力元エディター]** で、 **[エラー出力]** をクリックします。  
  
## <a name="options"></a>オプション  
  
### <a name="inputoutput"></a>[入力または出力]  
 データ ソースの名前を表示します。  
  
### <a name="column"></a>列  
 使用されていません。  
  
### <a name="error"></a>エラー  
 ODBC 入力元でフローのエラーを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### <a name="truncation"></a>切り捨て  
 ODBC 入力元でフローの切り捨てを処理する方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### <a name="description"></a>説明  
 使用されていません。  
  
### <a name="set-this-value-to-selected-cells"></a>[選択したセルに設定する値]  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルを ODBC 入力元でどのように処理するか (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を選択します。  
  
### <a name="apply"></a>適用  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="error-handling-options"></a>エラー処理オプション  
 ODBC 入力元でのエラーと切り捨ての処理方法を構成するには、次のオプションを使用します。  
  
### <a name="fail-component"></a>エラー コンポーネント  
 エラーまたは切り捨てが発生すると、データ フロー タスクは失敗します。 これは既定の動作です。  
  
### <a name="ignore-failure"></a>エラーを無視する  
 エラーまたは切り捨ては無視されます。  
  
### <a name="redirect-flow"></a>[フローのリダイレクト]  
 エラーまたは切り捨てが ODBC 入力元のエラー出力に送られる原因となった行。 詳しくは、「 [ODBC 入力元](data-flow/odbc-source.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [ODBC ソースエディター &#40;接続マネージャーのページ&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [[ODBC ソース エディター] &#40;[列] ページ&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)  
  
  
