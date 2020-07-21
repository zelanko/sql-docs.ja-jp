---
title: 整合性チェック |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edd946ca865cd9d8d2edff2c7bedbb3b2629c97c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299002"
---
# <a name="consistency-check"></a>整合性チェック
アプリケーションが APD、IPD、またはの SQL_DESC_DATA_PTR フィールドを設定するたびに、ドライバーによって整合性チェックが自動的に実行されます。 このフィールドが設定されている場合、ドライバーは、SQL_DESC_TYPE フィールドの値と、同じレコードの SQL_DESC_TYPE フィールドに適用できる値が有効で一貫性があることを確認します。  
  
 IPD の SQL_DESC_DATA_PTR フィールドは通常は設定されません。ただし、アプリケーションでは、IPD フィールドの整合性チェックを強制的に行うことができます。 IPD の SQL_DESC_DATA_PTR フィールドがに設定されている値は実際に格納されていないため、 **SQLGetDescField**または**Sqlgetdescrec**を呼び出すことによって取得することはできません。この設定は、整合性チェックを強制するためにのみ行われます。 IRD に対して整合性チェックを実行することはできません。  
  
 整合性チェックの詳細については、「 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)」を参照してください。
