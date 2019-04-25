---
title: 記述子フィールドの設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14724a5cc863074344cfbb02615f0ccff228f04c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447670"
---
# <a name="setting-descriptor-fields"></a>記述子フィールドの設定
記述子のフィールドを変更するには、アプリケーションを呼び出すことができます**SQLSetDescField**します。 一部のフィールドは読み取り専用と、設定することはできません。 (を参照してください、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)関数の説明です)。  
  
 レコード番号を持つ記述子レコードのフィールドが設定されます (*RecNumber*) レコード番号が 0 の 1 つ以上の while の記述子のヘッダー フィールドを設定します。 0 のレコード番号は、列 0 のブックマークが含まれている規則に従って、ブックマークのフィールドを設定するのにも使用されます。 これには、記述子のヘッダー内のブックマークのフィールドが含まれているが、そうでないこのような印象がままにします。 ブックマークのフィールドは、ヘッダー フィールドとは異なります。  
  
 定義されているシーケンスをアプリケーションが従う必要がありますフィールドを個別に設定するときに[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)します。 いくつかのフィールドに設定すると、他のフィールドを設定するドライバーと。 これにより、記述子は、アプリケーションのデータ型が指定した後で使用する準備が常にします。 SQL_DESC_TYPE フィールドを設定すると、アプリケーション、ドライバーは、型を指定するその他のフィールドが有効かつ一貫性のあることを確認します。  
  
 記述子フィールドを設定する関数呼び出しが失敗した場合、記述子フィールドの内容が失敗した関数呼び出しの後に定義できません。
