---
title: ODBC カーソル ライブラリ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b243e8ae2dc931830a249d4392da308e68722cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300052"
---
# <a name="the-odbc-cursor-library"></a>ODBC カーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ブロックカーソルとスクロール可能なカーソルは、多くのアプリケーションに非常に便利な追加です。 ただし、すべてのドライバーがブロックおよびスクロール可能なカーソルをサポートしているわけではありません。 同じことが、位置指定更新および削除ステートメントと**SQLSetPos**の場合も同様です。 したがって、以前は Microsoft データ アクセス コンポーネント (MDAC) SDK に含まれていた Windows SDK の ODBC コンポーネントには、カーソル ライブラリが含まれています。 カーソル ライブラリは、オープン グループ標準 CLI 準拠レベルを満たす任意のドライバーのブロック、静的カーソル、位置指定更新および削除ステートメント、および**SQLSetPos**を実装します。 カーソル ライブラリは ODBC アプリケーションで再配布できます。詳細については、SDK のライセンス契約を参照してください。  
  
 カーソル ライブラリを使用するには、アプリケーションは、データ ソースに接続する前にSQL_ATTR_ODBC_CURSORS接続属性を設定します。 カーソル ライブラリの詳細については、「[付録 F : ODBC カーソル ライブラリ](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md)」を参照してください。
