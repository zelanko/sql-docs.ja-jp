---
title: ディメンション処理変換先エディター (詳細 ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
caps.latest.revision: 27
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3947568a5fed3c2a2467741e93928380ba472e0a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254654"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a>[ディメンション処理変換先エディター] ([詳細設定] ページ)
  **[ディメンション処理変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理を構成できます。  
  
 ディメンション処理変換先の詳細については、「 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[既定のエラー構成を使用する]**  
 既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エラー処理を使用するかどうかを指定します。 既定では、この値は `True` です。  
  
 **[キー エラー アクション]**  
 許容されないキー値を持つレコードを処理する方法を指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**ConvertToUnknown**|許容できないキー値を `UnknownMember` 値に変換します。|  
|**DiscardRecord**|レコードを破棄します。|  
  
 **[エラーを無視する]**  
 エラーを無視することを指定します。  
  
 **[エラー時に停止する]**  
 エラーが発生した場合に処理を停止することを指定します。  
  
 **[エラー数]**  
 **[エラー時に停止する]** を選択した場合は、処理を停止するエラーのしきい値を指定します。  
  
 **[エラー時のアクション]**  
 **[エラー時に停止する]** を選択した場合は、エラーのしきい値に達した場合に実行する操作を指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**StopProcessing**|処理を停止します。|  
|**StopLogging**|ログ記録エラーを停止します。|  
  
 **[見つからないキー]**  
 見つからないキーのエラーに対する操作を指定します。 既定では、この値は **[ReportAndContinue]** です。  
  
|値|説明|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[重複キー]**  
 重複キーのエラーに対する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|Value|説明|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[不明な種類に変換された NULL キー]**  
 NULL キーが `UnknownMember` 値に変換された場合に実行する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|Value|説明|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[許可されていない NULL キー]**  
 NULL キーが許可されていない場合に NULL キーが検出されたときに実行する操作を指定します。 既定では、この値は **[ReportAndContinue]** です。  
  
|値|説明|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[エラー ログのパス]**  
 エラー ログのパスを入力するか、 **[…]** をクリックしてログの保存先を選択します。  
  
 **[...]**  
 エラー ログのパスを選択します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [ディメンション処理変換先エディター&#40;接続マネージャー ページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md)   
 [ディメンション処理変換先エディター&#40;マッピング ページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  
