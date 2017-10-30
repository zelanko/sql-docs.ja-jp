---
title: "スクリプト コンポーネントでイベントを発生させる |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 505855e82b683fc15ca00073f58e1f9cb348f830
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="raising-events-in-the-script-component"></a>スクリプト コンポーネントでのイベントの発生
  イベントは、エラーや警告、タスクの進行状況や状態などのその他の情報を、親パッケージにレポートする方法を提供するものです。 パッケージには、イベントの通知機能を管理するためのイベント ハンドラーがあります。 スクリプト コンポーネントは、イベントを発生させるメソッドを呼び出すことによって、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>のプロパティ、 **ScriptMain**クラスです。 方法の詳細についての[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]パッケージがイベントを処理を参照してください[Integration Services & #40 です。SSIS &#41;イベント ハンドラー](../../../integration-services/integration-services-ssis-event-handlers.md)です。  
  
 イベントは、パッケージ内で有効な任意のログ プロバイダーに記録できます。 ログ プロバイダーは、イベントに関する情報をデータ ストアに保存します。 スクリプト コンポーネントは、イベントを発生させずに <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを使用して、情報をログ プロバイダーに記録することもできます。 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドの使用方法の詳細については、次のセクションを参照してください。  
  
 イベントを発生させるには、スクリプト コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> プロパティによって公開される、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> インターフェイスの次のメソッドのいずれかを呼び出します。  
  
|イベント|Description|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|パッケージ内でユーザー定義のカスタム イベントを発生させます。|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|パッケージにエラー条件を通知します。|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|ユーザーに情報を提供します。|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|コンポーネントの進行状況をパッケージに通知します。|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|エラー条件ではないが、コンポーネントがユーザーに通知する必要がある状態であることをパッケージに通知します。|  
  
 エラー イベントを発生させる簡単な例を次に示します。  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;イベント ハンドラー](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [イベント ハンドラーをパッケージに追加します。](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  

