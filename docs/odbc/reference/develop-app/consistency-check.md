---
title: 整合性チェック |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299002"
---
# <a name="consistency-check"></a>整合性チェック
アプリケーションが APD、ARD、または IPD のSQL_DESC_DATA_PTR フィールドを設定するたびに、ドライバーによって整合性チェックが自動的に実行されます。 このフィールドが設定されるたびに、ドライバーは、SQL_DESC_TYPE フィールドの値と同じレコードのSQL_DESC_TYPEフィールドに適用される値が有効で一貫性があることを確認します。  
  
 IPD のSQL_DESC_DATA_PTRフィールドは、通常は設定されません。ただし、アプリケーションは IPD フィールドの整合性チェックを強制するためにこれを行うことができます。 IPD のSQL_DESC_DATA_PTRフィールドが設定されている値は実際には格納されず **、SQLGetDescField**または**SQLGetDescRec**の呼び出しでは取得できません。この設定は、整合性チェックを強制するためだけに行われます。 整合性チェックは、IRD では実行できません。  
  
 整合性チェックの詳細については、 [SQLSetDescRec を](../../../odbc/reference/syntax/sqlsetdescrec-function.md)参照してください。
