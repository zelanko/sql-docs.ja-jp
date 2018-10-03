---
title: 既定の優先順位制約を使用してタスクとコンテナーを連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c0c61c5db632121f99f8c22c8dd474d5597cb547
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221542"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a>既定の優先順位制約を使用してタスクとコンテナーを連結する
  優先順位制約は、2 つの実行可能ファイルを連結します。 実行可能ファイルには、任意のタスク、For ループ コンテナー、Foreach ループ コンテナー、またはシーケンス コンテナーが含まれます。 この手順では、優先順位制約の既定の動作を設定する方法と、既定の優先順位制約を使用して実行可能ファイルを連結する方法について説明します。  
  
## <a name="creating-default-precedence-constraints"></a>既定の優先順位制約の作成  
 使用すると[!INCLUDE[ssIS](../includes/ssis-md.md)]デザイナー、優先順位制約の既定値は`Success`します。 別の既定値を使用するように [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを構成するには、次の手順に従います。  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a>優先順位制約の既定値を設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。  
  
2.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
3.  **[オプション]** ダイアログ ボックスで **[ビジネス インテリジェンス デザイナー]** を展開し、次に **[Integration Services デザイナー]** を展開します。  
  
4.  **[制御フローの自動接続]** をクリックし、 **[選択した図形に新しい図形を既定で接続する]** をオンにします。  
  
5.  ドロップダウン リストで、 **[新しい図形に失敗制約を使用]** または **[新しい図形に完了制約を使用]** を選択します。  
  
6.  **[OK]** をクリックします。  
  
#### <a name="to-create-a-default-precedence-constraint"></a>既定の優先順位制約を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  **[制御フロー]** タブのデザイン画面で、タスクまたはコンテナーをクリックし、そのコネクタを、優先順位制約を適用する実行可能ファイルにドラッグします。  
  
5.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [優先順位制約](control-flow/precedence-constraints.md)   
 [ショートカット メニューを使用して、優先順位制約の値を設定します。](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [優先順位制約のプロパティを設定します。](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [優先順位制約で式を使用する](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
