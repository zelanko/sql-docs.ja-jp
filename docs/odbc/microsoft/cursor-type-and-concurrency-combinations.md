---
title: カーソルの種類と同時実行の組み合わせ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6397b5d675546bf41102f037b68c0022bec74df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280772"
---
# <a name="cursor-type-and-concurrency-combinations"></a>カーソルの種類およびコンカレンシーの組み合わせ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 カーソルの種類は、ユーザーに提供されるカーソルの機能を制御します。 同時実行オプションは、結果セットの更新可能性とロック動作を制御します。  
  
|カーソルの種類|同時実行 (許容値)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> [キーセット駆動型カーソルの使用に関する制限事項を](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md)参照してください。  
  
 <sup>[2]</sup> SQL_CONCUR_LOCKは、SQL_AUTOCOMMIT接続オプションがSQL_AUTOCOMMIT_OFFに設定されている場合にのみサポートされます。  
  
## <a name="see-also"></a>参照  
 [接続のオプション](../../odbc/microsoft/connect-options.md)
