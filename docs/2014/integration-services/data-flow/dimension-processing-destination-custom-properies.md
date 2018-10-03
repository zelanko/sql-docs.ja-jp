---
title: ディメンション処理変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39c6163234b5a874c90f853837440f5d18ae421d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209132"
---
# <a name="dimension-processing-destination-custom-properies"></a>ディメンション処理変換先のカスタム プロパティ
  ディメンション処理変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、ディメンション処理変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|KeyDuplicate|Integer (列挙)|UseDefaultConfiguration が`False`、重複キー エラーを処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0)。|  
|KeyErrorAction|Integer (列挙)|UseDefaultConfiguration が`False`、キー エラーを処理する方法を示す値。 有効な値は、`ConvertToUnknown` (0) および `DiscardRecord` (1) です。 このプロパティの既定値は`ConvertToUnknown`(0)。|  
|KeyErrorLimit|Integer|UseDefaultConfiguration が`False`、有効になっているキー エラーの上限値。|  
|KeyErrorLimitAction|Integer (列挙)|UseDefaultConfiguration が`False`、ときに実行するアクションを示す値`KeyErrorLimit`に到達します。 有効な値は、`StopLogging` (1) および `StopProcessing` (0) です。 このプロパティの既定値は`StopProcessing`(0)。|  
|KeyErrorLogFile|String|UseDefaultConfiguration が`False`、エラー ログ ファイルのパスとファイル名。|  
|KeyNotFound|Integer (列挙)|UseDefaultConfiguration が`False`、見つからないキーのエラーを処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0)。|  
|NullKeyConvertedToUnknown|Integer (列挙)|UseDefaultConfiguration が`False`、不明な値に変換された null キーを処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0)。|  
|NullKeyNotAllowed|Integer (列挙)|UseDefaultConfiguration が`False`、許容されない null の処理方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0)。|  
|ProcessType|Integer (列挙)|変換が使用するディメンション処理の種類。 値は、 `ProcessAdd` (1) (インクリメンタル)、 `ProcessFull` (0) と`ProcessUpdate`(2)。|  
|UseDefaultConfiguration|ブール値|変換が既定のエラー構成を使用するかどうかを指定する値。 このプロパティが場合`False`、変換には処理中にエラーに関する情報が含まれています。|  
  
 ディメンション処理変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [ディメンション処理変換先](dimension-processing-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
