---
title: ディメンション処理変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f4dae4c9661e8a04e34b5d2b78ccdd0f556bfa7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071721"
---
# <a name="dimension-processing-destination-custom-properies"></a>ディメンション処理変換先のカスタム プロパティ
  ディメンション処理変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、ディメンション処理変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|KeyDuplicate|Integer (列挙)|UseDefaultConfiguration が場合`False`、重複キー エラーを処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0) です。|  
|KeyErrorAction|Integer (列挙)|UseDefaultConfiguration が場合`False`、キーのエラーを処理する方法を示す値。 有効な値は、`ConvertToUnknown` (0) および `DiscardRecord` (1) です。 このプロパティの既定値は`ConvertToUnknown`(0) です。|  
|KeyErrorLimit|Integer|UseDefaultConfiguration が場合`False`、有効になっているキー エラーの数の上限。|  
|KeyErrorLimitAction|Integer (列挙)|UseDefaultConfiguration がある場合`False`、ときに実行するアクションを示す値`KeyErrorLimit`に到達します。 有効な値は、`StopLogging` (1) および `StopProcessing` (0) です。 このプロパティの既定値は`StopProcessing`(0) です。|  
|KeyErrorLogFile|String|UseDefaultConfiguration が場合`False`、エラー ログ ファイルのパスとファイル名。|  
|KeyNotFound|Integer (列挙)|UseDefaultConfiguration が場合`False`、存在しないというキー エラーを処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0) です。|  
|NullKeyConvertedToUnknown|Integer (列挙)|UseDefaultConfiguration が場合`False`、null キーを処理する方法を示す値を不明な値に変換します。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0) です。|  
|NullKeyNotAllowed|Integer (列挙)|UseDefaultConfiguration が場合`False`、許可されていない null を処理する方法を示す値。 指定できる値は`IgnoreError`(0)、 `ReportAndContinue` (1) と`ReportAndStop`(2)。 このプロパティの既定値は`IgnoreError`(0) です。|  
|ProcessType|Integer (列挙)|変換が使用するディメンション処理の種類。 値は、 `ProcessAdd` (1) (インクリメンタル)、 `ProcessFull` (0) と`ProcessUpdate`(2)。|  
|UseDefaultConfiguration|ブール値|変換が既定のエラー構成を使用するかどうかを指定する値。 このプロパティは、する場合`False`、変換には処理中にエラーに関する情報が含まれています。|  
  
 ディメンション処理変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [ディメンション処理変換先](dimension-processing-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  