---
title: データ型のサポート |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284429"
---
# <a name="data-type-support"></a>データ型のサポート
ODBC ドライバーは、少なくとも1つの SQL_CHAR と SQL_VARCHAR をサポートしている必要があります。 その他のデータ型のサポートは、ドライバーまたはデータソースの SQL-92 準拠レベルによって決まります。 アプリケーションは、 **SQLGetTypeInfo**を呼び出して、ドライバーでサポートされているデータ型を特定する必要があります。  
  
 データ型の詳細については、「[付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。
