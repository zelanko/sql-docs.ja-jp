---
title: スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c9380a9e8699b2c0f38436228b0a2fdf820096e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913390"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  この手順では、スクリプト タスクとスクリプト コンポーネントで使用するスクリプトに、ブレークポイントを設定する方法について説明します。  
  
 スクリプトにブレークポイントを設定すると、 **[ブレークポイントの設定 - \<object name>]** ダイアログ ボックスに、組み込みブレークポイントと共に、設定したブレークポイントの一覧が表示されるようになります。  
  
> [!IMPORTANT]  
>  状況によっては、スクリプト タスクおよびスクリプト コンポーネント内のブレークポイントは無視されます。 詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)」の「**スクリプト タスクのデバッグ**」セクションおよび「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」の「**スクリプト コンポーネントのデバッグ**」セクションを参照してください。  
  
### <a name="to-set-a-breakpoint-in-script"></a>スクリプトにブレークポイントを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ブレークポイントを設定するスクリプトを含むパッケージをダブルクリックします。  
  
3.  スクリプト タスクを開くには、 **[制御フロー]** タブをクリックして、スクリプト タスクをダブルクリックします。  
  
4.  スクリプト コンポーネントを開くには、 **[データ フロー]** タブをクリックして、スクリプト コンポーネントをダブルクリックします。  
  
5.  **[スクリプト]** をクリックし、 **[スクリプトの編集]** をクリックします。  
  
6.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) で、ブレークポイントを設定するスクリプト行を探して右クリックします。 **[ブレークポイント]** をポイントし、 **[ブレークポイントの挿入]** をクリックします。  
  
     ブレークポイントを表すアイコンがコード行に表示されます。  
  
7.  **[ファイル]** メニューの **[終了]** をクリックします。  
  
8.  **[OK]** をクリックします。  
  
9. パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
  
