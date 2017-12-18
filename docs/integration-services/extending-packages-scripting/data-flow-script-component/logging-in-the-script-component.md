---
title: "スクリプト コンポーネントでのログ記録 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c38888ad80d1674488a0335624997c0102e32d76
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="logging-in-the-script-component"></a>スクリプト コンポーネントでのログ記録
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのログ記録を使用すると、実行の進行状況、結果、問題点などに関する詳細な情報を、定義済みのイベントまたはユーザー定義のメッセージとして保存し、後で分析することができます。 スクリプト コンポーネントでユーザー定義のデータをログ記録するには、**ScriptMain** クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを使用できます。 ログ記録が有効で、**[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブでログ記録の対象として **[ScriptComponentLogEntry]** イベントが選択されている場合、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを 1 回呼び出すと、そのデータ フロー タスク用に設定されているすべてのログ プロバイダーに対し、イベント情報が保存されます。  
  
 ログ記録の簡単な例を次に示します。  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  ログ記録はスクリプト コンポーネントから直接実行できますが、ログ記録ではなくイベントを実装することを検討する必要があります。 イベントを使用すると、イベント メッセージのログ記録を有効にできるだけでなく、既定またはユーザー定義のイベント ハンドラーによってイベントに応答することができます。  
  
 ログ記録の詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
