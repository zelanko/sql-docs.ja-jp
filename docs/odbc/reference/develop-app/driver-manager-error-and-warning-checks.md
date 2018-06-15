---
title: ドライバー マネージャーのエラーおよび警告かどうか |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b411544e4d4ac54dc32cdbd126868f313b75c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908947"
---
# <a name="driver-manager-error-and-warning-checks"></a>ドライバー マネージャーのエラーと警告のチェック
ドライバー マネージャーは、完全または部分的には、関数の数を実装して、したがってエラーと警告のこれらの関数内のすべてまたは一部をチェックします。  
  
-   ドライバー マネージャーを実装する**SQLDataSources**と**SQLDrivers**され、すべてのエラーや警告のこれらの関数が確認されます。  
  
-   ドライバー マネージャーは、ドライバーが実装されているかどうかをチェック**SQLGetFunctions**です。 ドライバーを実装しない場合**SQLGetFunctions**、ドライバー マネージャーを実装し、すべてのエラーや警告のことを確認します。  
  
-   ドライバー マネージャーが部分的に実装する**SQLAllocHandle**、 **SQLConnect**、 **SQLDriverConnect**、 **SQLBrowseConnect**、 **SQLFreeHandle**、 **SQLGetDiagRec**、および**SQLGetDiagField**され、これらの関数のエラーの一部が確認されます。 どちらも同様の操作を実行するため、これらの関数の一部ではドライバーとして同じエラーが返さ可能性があります。 ドライバー マネージャーまたはドライバーが SQLSTATE IM008 を返す可能性があります、(に失敗しました ダイアログ ボックス) いずれか 1 つのログイン ダイアログ ボックスを表示することが**SQLDriverConnect**です。
