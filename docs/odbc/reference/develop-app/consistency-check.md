---
title: "整合性チェック |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f1148984210013a8d5c0c6d9096d04ac21141d2a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="consistency-check"></a>整合性チェック
アプリケーションが APD、ARD、または IPD の SQL_DESC_DATA_PTR フィールドを設定するたびに、整合性チェックは、ドライバーによって自動的に実行します。 このフィールドを設定すると、ドライバーは、SQL_DESC_TYPE フィールドの値と同じのレコードの SQL_DESC_TYPE フィールドに適用可能な値は、有効で一貫性のあることを確認します。  
  
 通常、IPD の SQL_DESC_DATA_PTR フィールドを設定がないです。ただし、アプリケーションでは、IPD フィールドの整合性チェックを強制的に行うことができます。 IPD の SQL_DESC_DATA_PTR フィールドに設定する値が実際に格納されていないとへの呼び出しによって取得することはできません**SQLGetDescField**または**SQLGetDescRec**; のみを強制的には、設定、整合性チェックです。 整合性チェックは、IRD では実行できません。  
  
 整合性チェックの詳細については、次を参照してください。 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)です。
