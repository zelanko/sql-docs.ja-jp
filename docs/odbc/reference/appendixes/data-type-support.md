---
title: データ型のサポート |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abfe85ee32fb9ff4a8499c9949c0685563fec70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284429"
---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバは、SQL_CHARとSQL_VARCHARの少なくとも 1 つをサポートしている必要があります。 その他のデータ型のサポートは、ドライバーまたはデータ ソースの SQL-92 準拠レベルによって決定されます。 アプリケーションは、ドライバーでサポートされているデータ型を決定する**SQLGetTypeInfo**を呼び出す必要があります。  
  
 データ型の詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。
