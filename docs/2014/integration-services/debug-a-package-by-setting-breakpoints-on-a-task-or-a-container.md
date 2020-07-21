---
title: タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3bf0956770823c4e3b70f90b03ef392568fedd2
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429749"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>タスクまたはコンテナーにブレークポイントを設定してパッケージをデバッグする
  この手順では、パッケージ、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーにブレークポイントを設定する方法について説明します。  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>パッケージ、タスク、またはコンテナーにブレークポイントを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ブレークポイントを設定するパッケージをダブルクリックします。  
  
3.  SSIS デザイナーで、次の操作を行います。  
  
    -   パッケージ オブジェクトにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、デザイン画面の背景の任意の場所にカーソルを置いて右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
    -   パッケージ制御フローにブレークポイントを設定するには、 **[制御フロー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
    -   イベント ハンドラーにブレークポイントを設定するには、 **[イベント ハンドラー]** タブをクリックし、タスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーを右クリックし、 **[ブレークポイントの編集]** をクリックします。  
  
4.  [**ブレークポイント \<container name> の設定**] ダイアログボックスで、有効にするブレークポイントを選択します。  
  
5.  必要に応じて、各ブレークポイントのヒット カウントの種類とヒット カウント数を変更します。  
  
6.  パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パッケージ開発のトラブルシューティングツール](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [スクリプトタスクとスクリプトコンポーネントにブレークポイントを設定してスクリプトをデバッグする](data-flow/transformations/script-component.md)   
 [スクリプトタスクのコーディングおよびデバッグ](control-flow/script-task.md)   
 [スクリプト コンポーネントのコーディングおよびデバッグ](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
