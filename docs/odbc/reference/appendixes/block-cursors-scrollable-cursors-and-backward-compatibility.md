---
title: ブロックカーソル、スクロール可能なカーソル、および下位互換性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe24362f1a49577a7fb494f768947080d0ab6e9e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292312"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>ブロック カーソル、スクロール可能なカーソル、および下位互換性
**SQLFetchScroll**と**SQLExtendedFetch**の両方の存在は、アプリケーション プログラミング インターフェイス (API) の間の ODBC で最初の明確な分割を表します。アプリケーションが呼び出す関数のセットであるサービス プロバイダー インターフェイス (SPI) は、ドライバーが実装する関数のセットです。 この分割は **、SQLFetchScroll**を使用する ODBC *3.x*が標準に準拠し **、SQLExtendedFetch**を使用する ODBC *2.x*とも互換性がある場合に必要です。  
  
 ODBC *3.x* API は、アプリケーションが呼び出す関数のセットであり **、SQLFetchScroll**および関連するステートメント属性を含みます。 ODBC *3.x* SPI は、ドライバーが実装する関数のセットであり **、SQLFetchScroll** **、SQLExtendedFetch**、および関連するステートメント属性を含みます。 ODBC では、API と SPI の間でこの分割が正式に強制されないため、ODBC *3.x*アプリケーションが**SQLExtendedFetch**および関連するステートメント属性を呼び出すことができます。 ただし、ODBC *3.x*アプリケーションがこれを行う理由はありません。 API と SIS の詳細については、「 ODBC[アーキテクチャ](../../../odbc/reference/odbc-architecture.md)の概要 」を参照してください。  
  
 ODBC *3.x*アプリケーションがブロックカーソルとスクロール可能カーソルで使用する関数およびステートメント属性については[、「ODBC 3.x アプリケーションのブロック カーソル、スクロール可能カーソル、および下位互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバー マネージャーの機能](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [ドライバーの機能](../../../odbc/reference/appendixes/what-the-driver-does.md)
