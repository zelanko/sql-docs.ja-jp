---
title: パーティション処理変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3dbab24f756498d7427f9961e4176249daac8dfb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62770948"
---
# <a name="partition-processing-destination-custom-properties"></a>パーティション処理変換先のカスタム プロパティ
  パーティション処理変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、パーティション処理変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスへの接続文字列。|  
|KeyDuplicate|Integer (列挙)|UseDefaultConfiguration が`False`の場合、重複キーエラーの処理方法を示す値です。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|KeyErrorAction|Integer (列挙)|UseDefaultConfiguration が`False`の場合、キーエラーの処理方法を示す値です。 有効な値は、`ConvertToUnknown` (0) および `DiscardRecord` (1) です。 このプロパティの既定値は `ConvertToUnknown` (0) です。|  
|KeyErrorLimit|整数|UseDefaultConfiguration が`False`の場合、許可されるキーエラーの上限です。|  
|KeyErrorLimitAction|Integer (列挙)|UseDefaultConfiguration が`False`の場合、に到達したとき`KeyErrorLimit`に実行するアクションを示す値。 有効な値は、`StopLogging` (1) および `StopProcessing` (0) です。 このプロパティの既定値は `StopProcessing` (0) です。|  
|KeyErrorLogFile|String|UseDefaultConfiguration がの`False`場合は、エラーログファイルのパスとファイル名を指定します。|  
|KeyNotFound|Integer (列挙)|UseDefaultConfiguration が`False`の場合、不足しているキーのエラーを処理する方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `ReportAndContinue` (1) です。|  
|NullKeyConvertedToUnknown|Integer (列挙)|UseDefaultConfiguration がの`False`場合、不明な値に変換された null キーの処理方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `IgnoreError` (0) です。|  
|NullKeyNotAllowed|Integer (列挙)|UseDefaultConfiguration がの`False`場合は、許可されていない null の処理方法を示す値。 有効な値は、`IgnoreError` (0)、`ReportAndContinue` (1)、および `ReportAndStop` (2) です。 このプロパティの既定値は `ReportAndContinue` (1) です。|  
|ProcessType|Integer (列挙)|変換が使用するパーティション処理の種類。 有効な値は、`ProcessAdd` (1) (インクリメンタル)、`ProcessFull` (0)、および `ProcessUpdate` (2) です。|  
|UseDefaultConfiguration|Boolean|変換が既定のエラー構成を使用するかどうかを指定する値。 このプロパティが`False`の場合、変換は、この表に示されているエラー処理カスタムプロパティの値 (keyduplicate、KeyErrorAction など) を使用します。|  
  
 パーティション処理変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [パーティション処理変換先](partition-processing-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
