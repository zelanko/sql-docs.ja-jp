---
title: ドライバー マネージャーのエラーと警告の確認 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e00b6907d58cda1708cf61907d3c5ff6bf56edfa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238030"
---
# <a name="driver-manager-error-and-warning-checks"></a>ドライバー マネージャーのエラーと警告の確認
ドライバー マネージャーは、完全または部分的には、多数の関数を実装して、そのためのエラーと警告のこれらの関数内のすべてまたは一部を確認します。  
  
-   ドライバー マネージャーを実装する**SQLDataSources**と**SQLDrivers**されすべてのエラーと警告のこれらの関数が確認されます。  
  
-   ドライバー マネージャーは、ドライバーを実装するかどうかを確認します。 **SQLGetFunctions**します。 ドライバーが実装していない場合**SQLGetFunctions**、ドライバー マネージャーを実装し、すべてのエラーと警告のことを確認します。  
  
-   ドライバー マネージャーを部分的に実装する**SQLAllocHandle**、 **SQLConnect**、 **SQLDriverConnect**、 **SQLBrowseConnect**、 **SQLFreeHandle**、 **SQLGetDiagRec**、および**SQLGetDiagField**とこれらの関数でいくつかのエラーが確認されます。 両方も同様の操作を実行するため、これらの関数の一部のドライバーとして同じエラーを返す、可能性があります。 ドライバー マネージャーやドライバーは SQLSTATE IM008 を返すなど (に失敗しました ダイアログ ボックス) 場合は、いずれか 1 つのログイン ダイアログ ボックスを表示することが**SQLDriverConnect**します。
