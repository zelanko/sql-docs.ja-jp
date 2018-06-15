---
title: 列のデータの長さ |Microsoft ドキュメント
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
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8075358f3675b201a7b8b0528b08de305bf587da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905699"
---
# <a name="length-of-column-data"></a>列のデータの長さ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリのキャッシュを使用して結果セットにバインドされた各長さ/インジケーター バッファーでバッファーを作成する**SQLBindCol**です。 これらのバッファーで構築するために、値を使用、**場所**位置指定更新をエミュレートまたは delete ステートメントの句。 位置指定の update ステートメントが実行されるときに、データ ソースからデータをフェッチにしたときに、これらのバッファー行セットのバッファーからを更新します。  
  
 データ バッファーの C 型が SQL_C_CHAR または SQL_C_BINARY、および長さ/インジケーター値は、SQL_NTS、データの文字列の長さは、長さ/インジケーター バッファーに配置されます。  
  
> [!NOTE]  
>  カーソル ライブラリが列のキャッシュを更新していない場合 **StrLen_or_IndPtr*バッファーが SQL_DATA_AT_EXEC または SQL_LEN_DATA_AT_EXEC マクロの結果には、対応する行セット内です。
