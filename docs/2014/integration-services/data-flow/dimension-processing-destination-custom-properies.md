---
title: ディメンション処理変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f37c189f4d71aa9201f87a0215a3e0fee331216c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437839"
---
# <a name="dimension-processing-destination-custom-properies"></a>ディメンション処理変換先のカスタム プロパティ
  ディメンション処理変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、ディメンション処理変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|KeyDuplicate|Integer (列挙)|UseDefaultConfiguration がの場合 `False` 、重複キーエラーの処理方法を示す値です。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|KeyErrorAction|Integer (列挙)|UseDefaultConfiguration がの場合 `False` 、キーエラーの処理方法を示す値。 有効な値は、`ConvertToUnknown` (0) および `DiscardRecord` (1) です。 このプロパティの既定値は `ConvertToUnknown` (0) です。|  
|KeyErrorLimit|整数|UseDefaultConfiguration がの場合 `False` 、有効になっているキーエラーの上限です。|  
|KeyErrorLimitAction|Integer (列挙)|UseDefaultConfiguration がの場合 `False` 、に到達したときに実行するアクションを示す値 `KeyErrorLimit` 。 有効な値は、`StopLogging` (1) および `StopProcessing` (0) です。 このプロパティの既定値は `StopProcessing` (0) です。|  
|KeyErrorLogFile|String|UseDefaultConfiguration がの場合は `False` 、エラーログファイルのパスとファイル名を指定します。|  
|KeyNotFound|Integer (列挙)|UseDefaultConfiguration がの場合 `False` 、不足しているキーのエラーを処理する方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|NullKeyConvertedToUnknown|Integer (列挙)|UseDefaultConfiguration がの場合 `False` 、不明な値に変換された null キーの処理方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|NullKeyNotAllowed|Integer (列挙)|UseDefaultConfiguration がの場合は `False` 、許可されていない null の処理方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|ProcessType|Integer (列挙)|変換が使用するディメンション処理の種類。 値は、( `ProcessAdd` 1) (増分)、 `ProcessFull` (0)、および `ProcessUpdate` (2) です。|  
|UseDefaultConfiguration|Boolean|変換が既定のエラー構成を使用するかどうかを指定する値。 このプロパティが `False` の場合、変換にはエラー処理に関する情報が含まれます。|  
  
 ディメンション処理変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [ディメンション処理変換先](dimension-processing-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
