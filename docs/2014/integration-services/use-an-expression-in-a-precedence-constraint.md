---
title: 優先順位制約で式を使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2fd5c1f75a0085767ade60f6010e446b70e60840
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972622"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a>優先順位制約で式を使用する
  この手順では、 **[優先順位制約エディター]** ダイアログ ボックスを使用して、優先順位制約に式を追加する方法について説明します。 優先順位制約に式を追加する場合、タスクまたはコンテナーのいずれかである実行可能ファイルを 2 つ以上含め、それらが優先順位制約によって連結される必要があります。  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>優先順位制約に式を追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  **[制御フロー]** タブのデザイン画面で、優先順位制約をダブルクリックします。 **[優先順位制約エディター]** が開きます。  
  
5.  **[評価操作]** の一覧で、 **[式]**、 **[式と制約]** 、または **[式または制約]** を選択します。  
  
6.  **[式]** ボックスに式を入力するか、式ビルダーを起動して式を作成します。  
  
7.  式の構文を検証するには、 **[テスト]** をクリックします。  
  
8.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [優先順位制約](control-flow/precedence-constraints.md)   
 [既定の優先順位制約を使用してタスクとコンテナーを連結する](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [ショートカットメニューを使用して優先順位制約の値を設定する](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Integration Services &#40;SSIS&#41; 式](expressions/integration-services-ssis-expressions.md)  
  
  
