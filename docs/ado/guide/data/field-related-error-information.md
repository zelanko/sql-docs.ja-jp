---
title: "フィールドに関連するエラー情報 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67404e4d66983c3cf64bd44a2d80c77c4eb99790
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="field-related-error-information"></a>フィールドに関連するエラー情報
エラーは、フィールドに直接関係する場合: たとえば、データが不足している場合、またはフィールドに対して無効な型である場合-を調べることによって、問題の原因に関する詳細を取得できます、**フィールド**オブジェクトの**ステータス**プロパティです。 このプロパティは、問題に関する情報を提供する拡張されています。 したがって、たとえばへの呼び出し時に**UpdateBatch**失敗した場合、問題の原因を調べることで決定できます、**ステータス**のプロパティ、**フィールド**の影響を受ける各レコードがあります。 内の値のいずれかのプロパティには、 **FieldStatusEnum**定数。 次の表には、エラーが発生したときに、特に関心があるはそれらの値が含まれています。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|フィールドを取得またはデータを失うことがなく保存できないことを示します。|  
|**adFieldDataOverflow**|6|プロバイダーから返されるデータがフィールドのデータ型をオーバーフローしたことを示します。|  
|**adFieldDefault**|13|フィールドの既定値がデータを設定するときに使用されることを示します。|  
|**adFieldIgnore**|15|このフィールドが、ソースで値のデータを設定時にスキップされたことを示します。 プロバイダーによって値が設定されていません。|  
|**adFieldIntegrityViolation**|10|計算された、または派生エンティティであるため、フィールドを変更できないことを示します。|  
|**adFieldIsNull**|3|プロバイダーが null 値を返すことを示します。|  
|**adFieldOutOfSpace**|22|プロバイダーが、移動が完了またはコピー操作に十分な記憶域を入手することであることを示します。|
