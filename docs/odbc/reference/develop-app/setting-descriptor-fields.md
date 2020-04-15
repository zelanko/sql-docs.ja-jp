---
title: 記述子フィールドの設定 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04f9520e2ef462df481bb104e389aeb57b5dd457
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304153"
---
# <a name="setting-descriptor-fields"></a>記述子フィールドの設定
記述子のフィールドを変更するには、アプリケーションは**SQLSetDescField**を呼び出すことができます。 一部のフィールドは読み取り専用で、設定できません。 (関数の説明[を](../../../odbc/reference/syntax/sqlsetdescfield-function.md)参照してください。  
  
 記述子レコード・フィールドはレコード番号 (*RecNumber*) が 1 以上で設定され、記述子ヘッダー・フィールドはレコード番号 0 で設定されます。 レコード番号 0 は、ブックマークが列 0 に含まれるという規則に従って、ブックマーク フィールドを設定するためにも使用されます。 これにより、ブックマークフィールドが記述子ヘッダー内に含まれているという印象が残る場合がありますが、これはそうではありません。 ブックマーク フィールドは、ヘッダー フィールドとは異なります。  
  
 フィールドを個別に設定する場合、アプリケーションは[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)で定義されている順序に従う必要があります。 一部のフィールドを設定すると、ドライバーは他のフィールドを設定します。 これにより、アプリケーションがデータ型を指定した後で、記述子を常に使用できるようになります。 アプリケーションがSQL_DESC_TYPE フィールドを設定すると、ドライバーは、型を指定する他のフィールドが有効で一貫性があることを確認します。  
  
 記述子フィールドを設定する関数呼び出しが失敗した場合、記述子フィールドの内容は、失敗した関数呼び出しの後に未定義になります。
