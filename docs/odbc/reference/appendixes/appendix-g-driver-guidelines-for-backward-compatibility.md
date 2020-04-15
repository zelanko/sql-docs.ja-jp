---
title: '付録 G: 下位互換性のためのドライバガイドライン |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1055f94cb54bba9262f210e5df5f028029aebf5b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292402"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>付録 G: ドライバーの下位互換性のガイドライン
この付録では、ODBC 3 で作業するドライバー作成者向けの情報を提供します。ODBC 2 をサポートする必要がある*x*ドライバ。*x*アプリケーション。 下位互換性の詳細については、「[下位互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC 3.x ドライバのブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)- 新機能は ODBC 3 に存在する機能です。*x*で、ODBC 2 では使用しません。*x .* ODBC 3.*x*ドライバは、一般に、ODBC 2 の新機能との下位互換性を心配する必要はありません。*x*アプリケーションは決してそれらを使用しません。 この唯一の例外は **、SQL フェッチ** **、SQL フェッチスクロール****、SQL セットPos**、および**SQLExtendedFetch**に関連する機能です。詳細については、この付録の「 」を参照してください。  
  
-   [マッピング非推奨関数](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)- 重複した機能は、ODBC 3 で異なる方法で実装される機能です。*x*と ODBC 2。*x .* ODBC 3.*x*ドライバは、ドライバ マネージャが常に ODBC 2 をマップするため、重複した機能との下位互換性を心配する必要はありません。*x*は ODBC 3 に対して機能します。ODBC 3 を呼び出すときの*x*機能。*x*ドライバ。 したがって、ODBC 3。*x*ドライバには ODBC 3 のみが表示されます。*x*の特徴。 これらのマッピングの詳細については、この付録の「 」を参照してください。  
  
-   [動作の変更と ODBC 3.x ドライバー](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) - 動作の変更は ODBC 3 で異なる処理を行う機能です。*x*と ODBC 2。*x .* ODBC 3.*x*ドライバは、動作の変更を心配し、アプリケーションによって設定されたSQL_ATTR_ODBC_VERSION環境属性に応じて動作する必要があります。
