---
title: ブロックカーソル、スクロール可能なカーソル、および旧バージョンとの互換性 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292312"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>ブロック カーソル、スクロール可能なカーソル、および下位互換性
**Sqlfetchscroll**と**SQLExtendedFetch**の両方が存在する場合は、アプリケーションプログラミングインターフェイス (API) と、アプリケーションが呼び出す一連の関数、およびドライバーが実装する関数のセットである SERVICE Provider Interface (SPI) との間の、ODBC での最初の clear split を表します。 この分割は、ODBC 3.x で**Sqlfetchscroll**を使用し、標準に準拠していて、 **SQLExtendedFetch***を使用**する odbc 2.x*と互換性があるようにするために必要です。  
  
 ODBC 3.x API は、アプリケーションが呼び出す関数のセットであり、 **Sqlfetchscroll**および関連するステートメント属性が含まれてい*ます。* ODBC 3.x はドライバーが実装する関数のセットであり、 **Sqlfetchscroll**、 **SQLExtendedFetch**、および関連するステートメント属性が含まれて*います。* ODBC では API と SPI の間にこの分割が正式に適用されないため、ODBC 3.x アプリケーションは**SQLExtendedFetch**および関連するステートメント属性を呼び出すことが*できます。* ただし、この操作を行うのは*ODBC 3.x*アプリケーションの理由ではありません。 Api と Spi の詳細については、「 [ODBC アーキテクチャ](../../../odbc/reference/odbc-architecture.md)の概要」を参照してください。  
  
 *Odbc 3.x*アプリケーションでブロックおよびスクロール可能なカーソルと共に使用する関数およびステートメント属性の詳細については、「[ブロックカーソル、スクロール可能なカーソル、および odbc 3. x アプリケーションの旧バージョンとの互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバー マネージャーの機能](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [ドライバーの機能](../../../odbc/reference/appendixes/what-the-driver-does.md)
