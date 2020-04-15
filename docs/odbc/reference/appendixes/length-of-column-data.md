---
title: 列データの長さ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0b7ad515661cce4c5b1d407be768cc3da131bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304933"
---
# <a name="length-of-column-data"></a>列データの長さ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは **、SQLBindCol**を使用して結果セットにバインドされた各長さ/インジケーター バッファーのキャッシュにバッファーを作成します。 位置指定更新または削除ステートメントをエミュレートするときに、これらのバッファー内の値を使用して**WHERE**句を作成します。 データ ソースからデータをフェッチするとき、および位置指定更新ステートメントを実行するときに、行セット バッファーからこれらのバッファーを更新します。  
  
 データバッファのC型がSQL_C_CHARまたはSQL_C_BINARYで、長さ/インジケーター値がSQL_NTS場合、データの文字列長は長さ/インジケーターバッファに入れられます。  
  
> [!NOTE]  
>  対応する行セット バッファーの*StrLen_or_IndPtrが*SQL_DATA_AT_EXEC、またはSQL_LEN_DATA_AT_EXEC マクロの結果である場合、カーソル ライブラリは列のキャッシュを更新しません。
