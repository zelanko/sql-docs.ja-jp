---
title: "ディメンション処理変換先エディター (詳細 ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81e97a5a5e653fb02f0e8a1ccc5741bb3e86acf1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="dimension-processing-destination-editor-advanced-page"></a>[ディメンション処理変換先エディター] ([詳細設定] ページ)
  **[ディメンション処理変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理を構成できます。  
  
 ディメンション処理変換先の詳細については、「 [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[既定のエラー構成を使用する]**  
 既定の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラー処理を使用するかどうかを指定します。 既定では、この値は **True**です。  
  
 **[キー エラー アクション]**  
 許容されないキー値を持つレコードを処理する方法を指定します。  
  
|Value|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|不正なキー値を **UnknownMember** に変換します。|  
|**DiscardRecord**|レコードを破棄します。|  
  
 **[エラーを無視する]**  
 エラーを無視することを指定します。  
  
 **[エラー時に停止する]**  
 エラーが発生した場合に処理を停止することを指定します。  
  
 **[エラー数]**  
 **[エラー時に停止する]**を選択した場合は、処理を停止するエラーのしきい値を指定します。  
  
 **「エラー時のアクション**  
 **[エラー時に停止する]**を選択した場合は、エラーのしきい値に達した場合に実行する操作を指定します。  
  
|Value|Description|  
|-----------|-----------------|  
|**StopProcessing**|処理を停止します。|  
|**StopLogging**|ログ記録エラーを停止します。|  
  
 **[見つからないキー]**  
 見つからないキーのエラーに対する操作を指定します。 既定では、この値は **[ReportAndContinue]**です。  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[重複キー]**  
 重複キーのエラーに対する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[不明な種類に変換された NULL キー]**  
 NULL キーが **UnknownMember** 値に変換された場合に実行する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[許可されていない NULL キー]**  
 NULL キーが許可されていない場合に NULL キーが検出されたときに実行する操作を指定します。 既定では、この値は **[ReportAndContinue]**です。  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**[ReportAndContinue]**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **[エラー ログのパス]**  
 エラー ログのパスを入力するか、 **[…]** をクリックしてログの保存先を選択します。  
  
 **[...]**  
 エラー ログのパスを選択します。  
  
## <a name="see-also"></a>「  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [ディメンション処理変換先エディターと &#40; です。接続マネージャー」 ページと &#41; です。](../../integration-services/data-flow/dimension-processing-destination-editor-connection-manager-page.md)   
 [ディメンション処理変換先エディターと &#40; です。「マッピング」 ページと &#41; です。](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)  
  
  
