---
title: "付録 g: 旧バージョンとの互換性のためドライバー ガイドライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e326abbc0a10899028bf93d27f219fadd8d7dd29
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>旧バージョンとの互換性のための付録 g: ドライバーのガイドライン
この付録では、ドライバーの作成者が ODBC 3 での作業の情報を提供します。*x* ODBC 2 をサポートするために必要なドライバー* 。x*アプリケーションです。 旧バージョンと互換性の詳細については、次を参照してください。[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ブロック カーソル、スクロール可能なカーソル、および ODBC 3.x ドライバーとの下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)— 新機能は、ODBC 3 に存在する機能*。x* ODBC 2 ではなく*。x*です。 ODBC 3 です。*x*ドライバー通常必要はありませんので、新機能との下位互換性について心配する ODBC 2* 。x*しないアプリケーションで使用します。 唯一の例外に関連する機能は、 **SQLFetch**、 **SQLFetchScroll**、 **SQLSetPos**、および**SQLExtendedFetch**詳細です。については、この付録の「を参照してください。  
  
-   [非推奨の関数のマップ](../../../odbc/reference/appendixes/mapping-deprecated-functions.md): 重複する機能は、ODBC 3 に異なる方法で実装されている機能です*。x*および ODBC 2* 。x*です。 ODBC 3 です。*x*ドライバーは、ドライバー マネージャーは、ODBC 2 を常にマップされるので、重複する機能との下位互換性について心配する必要はありません*。x* ODBC 3 に機能します*。x* ODBC 3 を呼び出すときに機能します*。x*ドライバー。 したがって、ODBC 3 です。*x*ドライバーは ODBC 3 のみを表示します*。x*機能します。 詳細については、これらのマッピング後の「を参照してください。  
  
-   [動作の変更と ODBC 3.x ドライバー](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) — 動作の変更は、ODBC 3 が異なる方法で処理する機能*。x*および ODBC 2* 。x*です。 ODBC 3 です。*x*ドライバーは、動作の変更について心配し、アプリケーションによって設定される、また環境属性への応答で操作する必要があります。

