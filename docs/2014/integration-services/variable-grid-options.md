---
title: 可変グリッドのオプション |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.variableoptionswindow.f1
helpviewer_keywords:
- Choose Variable Columns dialog box
ms.assetid: 7cccc230-3b20-4074-804f-3448d9616a83
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3ef640f5aadc018702c9141de97e18e1920edb8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085016"
---
# <a name="variable-grid-options"></a>可変グリッドのオプション
  **[可変グリッドのオプション]** ダイアログ ボックスを使用して、 **[変数]** ウィンドウに表示される列を選択したり、変数の一覧に適用するフィルターを選択したりします。 対応する変数のプロパティの詳細については、次を参照してください。 [Integration Services &#40;SSIS&#41;変数](integration-services-ssis-variables.md)です。  
  
## <a name="options-for-filter"></a>フィルターのオプション  
 **システム変数を表示する**  
 選択すると、 **[変数]** ウィンドウにシステム変数が一覧表示されます。 システム変数は定義済みです。 システム変数は追加も削除もできません。 **RaiseChangedEvent** プロパティ設定を変更できます。  
  
 この一覧は色分け表示されています。 システム変数は灰色で、ユーザー定義変数は黒です。  
  
 **すべてのスコープの変数を表示する**  
 選択すると、パッケージのスコープ内の変数、および、パッケージにあるコンテナー、タスク、およびイベント ハンドラーのスコープ内の変数が表示されます。 このオプションをオフにすると、パッケージのスコープ内の変数、および、選択されたコンテナー、タスク、またはイベント ハンドラーのスコープ内の変数のみが表示されます。  
  
 変数のスコープの詳細については、次を参照してください。 [Integration Services &#40;SSIS&#41;変数](integration-services-ssis-variables.md)です。  
  
## <a name="options-for-columns"></a>列のオプション  
 **[変数]** ウィンドウに表示する列を選択します。  
  
-   **スコープ**  
  
-   **Data type**  
  
-   **Value**  
  
-   **Namespace**  
  
-   **[変数値の変化時にイベントを発生]**  
  
-   **description**  
  
-   **[式]**  
  
## <a name="see-also"></a>参照  
 [[変数] ウィンドウ](../../2014/integration-services/variables-window.md)   
 [Integration Services &#40;SSIS&#41;変数](integration-services-ssis-variables.md)   
 [パッケージの変数を使用します。](../../2014/integration-services/use-variables-in-packages.md)   
 [Integration Services &#40;SSIS&#41;イベント ハンドラー](integration-services-ssis-event-handlers.md)  
  
  