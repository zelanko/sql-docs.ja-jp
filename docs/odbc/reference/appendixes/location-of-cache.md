---
title: キャッシュの場所 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 13510332ae8bfab07a13d7831f9f74a048551214
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288620"
---
# <a name="location-of-cache"></a>キャッシュの場所
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリは、メモリ内および Windows ®一時ファイル内のデータをキャッシュします。 これにより、カーソル ライブラリが使用可能なディスク領域によってのみ処理できる結果セットのサイズが制限されます。 一時ファイルは、キャッシュされるデータが、カーソル ライブラリ キャッシュの最後に挿入された場合にセグメント境界を越える場合に使用されます。 代わりに、キャッシュされるデータは、キャッシュ内の最後に保存されたデータ ブロックの代わりに追加されます。 最後に保存されたデータブロックは、一時ファイルに保存されます。 電源が切れた場合など、カーソル ライブラリが異常終了した場合、Windows の一時ファイルがディスク上に残る可能性があります。 これらは ~CTT*nnnn*.tmp という名前で、現在のディレクトリに作成されます。  
  
> [!NOTE]  
>  Microsoft® のカーソル ライブラリが®読み取り専用共有またはコンパクト ディスク (Microsoft Foundation クラス ライブラリサンプルなど) から実行されている間に、現在のディレクトリの一時ファイルにデータをキャッシュしようとすると、SQLSTATE HY000 (一般エラー - ファイル バッファを作成できません) が返されます。
