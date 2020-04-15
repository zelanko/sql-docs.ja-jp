---
title: 固定長ブックマーク |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306983"
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
ODBC *3.x*ドライバーが固定長のブックマークを使用する ODBC *2.x*アプリケーションで動作する必要がある場合、ドライバーは次をサポートする必要があります。  
  
-   SQL_USE_BOOKMARKSステートメント・オプションの値としてSQL_UB_ONします。 (SQL_UB_ONは ODBC *3.x*では非推奨です。  
  
-   SQL_GET_BOOKMARK ステートメント オプション。
