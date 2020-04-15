---
title: ドライバ マネージャのエラーと警告のチェック |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee8a0f5ebfac8b6f87281806f07989f4980eb9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305784"
---
# <a name="driver-manager-error-and-warning-checks"></a>ドライバー マネージャーのエラーと警告の確認
ドライバ マネージャは、いくつかの機能を完全または部分的に実装しているため、これらの関数のエラーと警告の全部または一部をチェックします。  
  
-   ドライバー マネージャーは **、SQL データソース**と**SQL ドライバー**を実装し、これらの関数のすべてのエラーと警告をチェックします。  
  
-   ドライバー マネージャーは、ドライバーが**SQLGetFunctions**を実装するかどうかを確認します。 ドライバーが実装しない場合**は、** ドライバー マネージャーを実装し、その中のすべてのエラーと警告をチェックします。  
  
-   ドライバー マネージャーは部分的に**SQLAllocHandle、SQLConnect、SQL****ドライバー接続****、SQL ブラウズ接続、SQL****フリーハンドル、SQLGetDiagRec**、および**SQLConnect****SQLGetDiagField**を実装し、これらの関数のいくつかのエラーをチェックします。 **SQLGetDiagRec** 両方とも同様の操作を実行するため、これらの関数の一部のドライバーと同じエラーが返される場合があります。 たとえば、どちらかの**SQLDriverConnect**のログイン ダイアログ ボックスを表示できない場合、ドライバー マネージャーまたはドライバーは SQLSTATE IM008 (ダイアログ に失敗しました) を返す可能性があります。
