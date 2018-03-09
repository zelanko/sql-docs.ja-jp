---
title: "パーティション処理変換先のカスタム プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a4ed16b65d8f6c7096551f7a55382e97213c9da
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="partition-processing-destination-custom-properties"></a>パーティション処理変換先のカスタム プロパティ
  パーティション処理変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、パーティション処理変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスへの接続文字列。|  
|KeyDuplicate|Integer (列挙)|UseDefaultConfiguration が **False**の場合、重複キー エラーの処理方法を示す値。 指定できる値は **IgnoreError** (0)、 **ReportAndContinue** (1)、 **ReportAndStop** (2) です。 このプロパティの既定値は **IgnoreError** (0) です。|  
|KeyErrorAction|Integer (列挙)|UseDefaultConfiguration が **False**である場合に、キー エラーを処理する方法を示す値。 指定できる値は **ConvertToUnknown** (0) と **DiscardRecord** (1) です。 このプロパティの既定値は **ConvertToUnknown** (0) です。|  
|KeyErrorLimit|Integer|UseDefaultConfiguration が **False**である場合に、許可されるキー エラーの数の上限。|  
|KeyErrorLimitAction|Integer (列挙)|UseDefaultConfiguration が **False**である場合、 **KeyErrorLimit** に到達したときに実行するアクションを示す値。 指定できる値は **StopLogging** (1) と **StopProcessing** (0) です。 このプロパティの既定値は **StopProcessing** (0) です。|  
|KeyErrorLogFile|String|UseDefaultConfiguration が **False**である場合、エラー ログ ファイルのパスとファイル名。|  
|KeyNotFound|Integer (列挙)|UseDefaultConfiguration が **False**である場合、見つからないキーのエラーを処理する方法を示す値。 指定できる値は **IgnoreError** (0)、 **ReportAndContinue** (1)、 **ReportAndStop** (2) です。 このプロパティの既定値は **ReportAndContinue** (1) です。|  
|NullKeyConvertedToUnknown|Integer (列挙)|UseDefaultConfiguration が **False**の場合、不明な値に変換された NULL キーの処理方法を示す値。 指定できる値は **IgnoreError** (0)、 **ReportAndContinue** (1)、 **ReportAndStop** (2) です。 このプロパティの既定値は **IgnoreError** (0) です。|  
|NullKeyNotAllowed|Integer (列挙)|UseDefaultConfiguration が **False**である場合、許容されない NULL を処理する方法を示す値。 指定できる値は **IgnoreError** (0)、 **ReportAndContinue** (1)、 **ReportAndStop** (2) です。 このプロパティの既定値は **ReportAndContinue** (1) です。|  
|processType|Integer (列挙)|変換が使用するパーティション処理の種類。 指定できる値は **ProcessAdd** (1) (インクリメンタル)、 **ProcessFull** (0)、 **ProcessUpdate** (2) です。|  
|UseDefaultConfiguration|ブール値|変換が既定のエラー構成を使用するかどうかを指定する値。 このプロパティが **False**の場合、変換は、この表の一覧で示されている、KeyDuplicate や KeyDuplicate などのエラー処理のカスタム プロパティの値を使用します。|  
  
 パーティション処理変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [パーティション処理変換先](../../integration-services/data-flow/partition-processing-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
