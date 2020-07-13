---
title: SqlTriggerContext オブジェクト |Microsoft Docs
description: SQL Server CLR 統合では、SqlTriggerContext クラスによって、アクションの種類や操作中に変更された列などのトリガーのコンテキスト情報が提供されます。
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 4634a0c95e64516b6364fbfd68edeb9cd6156511
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765417"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext オブジェクト
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  **Sqltriggercontext**クラスは、トリガーに関するコンテキスト情報を提供します。 このコンテキスト情報には、トリガーを起動する原因となったアクションの種類、更新操作で変更された列、データ定義言語 (DDL) トリガーの場合は、トリガー操作を記述する XML **EventData**構造が含まれます。 **Sqltriggercontext**クラスの使用方法の詳細と例については、「 [CLR Triggers](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)」を参照してください。  
  
 詳細については、.NET Framework SDK ドキュメントの「 **Microsoft Sql server のコンテキスト**クラスのリファレンスドキュメント」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [CLR トリガー](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
