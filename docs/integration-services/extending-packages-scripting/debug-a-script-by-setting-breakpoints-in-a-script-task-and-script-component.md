---
title: "スクリプト タスクおよびスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96815b337311c4ba8d16e10c25891c728e7a0c74
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする
  この手順では、スクリプト タスクとスクリプト コンポーネントで使用するスクリプトに、ブレークポイントを設定する方法について説明します。  
  
 スクリプトでは、ブレークポイントを設定した後、**ブレークポイントの設定 -\<オブジェクト名 >**  ダイアログ ボックスに、組み込みブレークポイントと共に、ブレークポイントが一覧表示されます。  
  
> [!IMPORTANT]  
>  状況によっては、スクリプト タスクおよびスクリプト コンポーネント内のブレークポイントは無視されます。 詳細については、次を参照してください。、**スクリプト タスクのデバッグ**」の「[コーディングし、スクリプト タスクのデバッグ](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)と**スクリプト コンポーネントのデバッグ**」の「[コーディングおよびスクリプト コンポーネントのデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)です。  
  
### <a name="to-set-a-breakpoint-in-script"></a>スクリプトにブレークポイントを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ブレークポイントを設定するスクリプトを含むパッケージをダブルクリックします。  
  
3.  スクリプト タスクを開くをクリックして、**制御フロー**タブをクリックし、スクリプト タスクをダブルクリックします。  
  
4.  スクリプト コンポーネントを開くをクリックして、**データ フロー**タブをクリックし、スクリプト コンポーネントをダブルクリックします。  
  
5.  をクリックして**スクリプト** をクリックし、**スクリプトの編集**です。  
  
6.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)、ブレークポイントを設定、その行を右クリックし] をポイントするスクリプトの行を検索する**ブレークポイント**、クリックして**ブレークポイントの挿入**です。  
  
     ブレークポイントを表すアイコンがコード行に表示されます。  
  
7.  **[ファイル]** メニューの **[終了]**をクリックします。  
  
8.  **[OK]**をクリックします。  
  
9. パッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
  
