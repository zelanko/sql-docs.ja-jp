---
title: 列データ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff89566efa65c88325d98422fe17788f27d2c8ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306593"
---
# <a name="column-data"></a>列のデータ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは **、SQLBindCol**を使用して結果セットにバインドされた各データ バッファーのキャッシュにバッファーを作成します。 位置指定更新または削除ステートメントをエミュレートするときに、これらのバッファー内の値を使用して**WHERE**句を作成します。 データ ソースからデータをフェッチするとき、および位置指定更新ステートメントを実行するときに、行セット バッファーからこれらのバッファーを更新します。  
  
 カーソル ライブラリが行セット バッファからキャッシュを更新すると **、SQLBindCol**で指定された C データ型に従ってデータが転送されます。 たとえば、行セット バッファーの C データ型がSQL_C_SLONG場合、カーソル ライブラリは 4 バイトのデータを転送します。SQL_C_CHARで*BufferLength*が 10 の場合、カーソル ライブラリは 10 バイトのデータを転送します。 カーソル ライブラリは、転送するデータに対して型チェックや変換を行いません。  
  
> [!NOTE]  
>  対応する行セット バッファーの*StrLen_or_IndPtrが*SQL_DATA_AT_EXEC、またはSQL_LEN_DATA_AT_EXEC マクロの結果である場合、カーソル ライブラリは列のキャッシュを更新しません。  
  
 列を更新すると、データ・ソースは固定長の文字データと、必要に応じて固定長の固定長のバイナリー・データをブランクパッドで埋めます。 たとえば、データ ソースは"スミス" を CHAR(10) 列に "Smith" として格納します。 カーソル ライブラリは、位置指定更新ステートメントの実行後にこのデータをキャッシュにコピーするときに、行セット バッファー内の空白パッドまたはゼロパッドのデータを行いません。 したがって、アプリケーションがカーソル ライブラリのキャッシュ内の値を空白埋め込みまたはゼロパッドで埋める必要がある場合は、位置指定更新ステートメントを実行する前に行セット バッファーの値を空白埋め込みまたはゼロパッドで埋める必要があります。
