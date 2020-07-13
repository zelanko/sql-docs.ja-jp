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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04f9520e2ef462df481bb104e389aeb57b5dd457
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304153"
---
# <a name="setting-descriptor-fields"></a>記述子フィールドの設定
記述子のフィールドを変更するには、アプリケーションで**SQLSetDescField**を呼び出すことができます。 一部のフィールドは読み取り専用であり、設定することはできません。 ( [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)関数の説明を参照してください)。  
  
 記述子のレコードフィールドは1以上のレコード番号 (*recnumber*) で設定されますが、記述子ヘッダーフィールドはレコード番号0で設定されます。 ブックマークが列0に含まれるという規則に従って、レコード番号0を使用してブックマークフィールドを設定することもできます。 これにより、ブックマークフィールドが記述子ヘッダー内に含まれているように見える場合がありますが、そうではありません。 ブックマークフィールドは、ヘッダーフィールドとは異なります。  
  
 フィールドを個別に設定する場合、アプリケーションは[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)で定義されているシーケンスに従う必要があります。 一部のフィールドを設定すると、ドライバーによって他のフィールドが設定されます。 これにより、アプリケーションがデータ型を指定した後、常に記述子を使用できるようになります。 アプリケーションが SQL_DESC_TYPE フィールドを設定すると、ドライバーは、その種類を指定する他のフィールドが有効で一貫性があることを確認します。  
  
 記述子フィールドを設定する関数呼び出しが失敗した場合、失敗した関数呼び出しの後に、記述子フィールドの内容が未定義になります。
