---
title: スクリプト コンポーネントでのイベントの発生 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88cbe69d39ffd0d76ea0a14f185ce537595fa57d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426129"
---
# <a name="raising-events-in-the-script-component"></a>スクリプト コンポーネントでのイベントの発生
  イベントは、エラーや警告、タスクの進行状況や状態などのその他の情報を、親パッケージにレポートする方法を提供するものです。 パッケージには、イベントの通知機能を管理するためのイベント ハンドラーがあります。 スクリプト コンポーネントは、`ScriptMain` クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティに対してメソッドを呼び出して、イベントを発生させることができます。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのイベントの処理の詳細については、「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md)」を参照してください。  
  
 イベントは、パッケージ内で有効な任意のログ プロバイダーに記録できます。 ログ プロバイダーは、イベントに関する情報をデータ ストアに保存します。 スクリプト コンポーネントは、イベントを発生させずに <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを使用して、情報をログ プロバイダーに記録することもできます。 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドの使用方法の詳細については、次のセクションを参照してください。  
  
 イベントを発生させるには、スクリプト コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> プロパティによって公開される、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> インターフェイスの次のメソッドのいずれかを呼び出します。  
  
|Event|説明|  
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
  
![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>関連項目  
 [SSIS&#41; イベントハンドラーの Integration Services &#40;](../../integration-services-ssis-event-handlers.md)   
 [パッケージにイベント ハンドラーを追加する](../../add-an-event-handler-to-a-package.md)  
  
  
