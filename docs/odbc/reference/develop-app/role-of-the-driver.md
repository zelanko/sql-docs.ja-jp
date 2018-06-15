---
title: ドライバーの役割 |Microsoft ドキュメント
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
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e0ef812cb4c397beeb5778c4e4764b7e79f5d0a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910667"
---
# <a name="role-of-the-driver"></a>ドライバーのロール
ドライバーは、すべてのエラーと警告をオフに、ドライバー マネージャーで確認し、生成された状態レコードを orders します。 (ODBC 2 です。*x*ドライバーには、状態レコードは順序付けしません)。データの切り捨て、データ変換、構文、およびいくつかの状態遷移のエラーと警告が含まれます。 エラーと警告が部分的にチェック ドライバー マネージャーによって、ドライバーはチェックも可能性があります。 たとえば、ドライバー マネージャーのチェックがかどうかの値*操作*で**SQLSetPos**は法律、ドライバーがサポートされているかどうかを確認する必要があります。  
  
 ドライバーもマップ*ネイティブ エラー* — データ ソースによって返されたエラーは、— SQLSTATEs にします。 たとえば、ドライバーは、無効な SQL 構文を SQLSTATE 42000 (構文エラーまたはアクセス違反) のさまざまなネイティブ エラー番号をマップする可能性があります。 ドライバーは、状態レコードの SQL_DIAG_NATIVE フィールドに、ネイティブ エラー番号を返します。 ドライバーのドキュメントがの引数に、データ ソースからのエラーと警告のマップ方法を説明する必要があります**SQLGetDiagRec**と**SQLGetDiagField**です。
