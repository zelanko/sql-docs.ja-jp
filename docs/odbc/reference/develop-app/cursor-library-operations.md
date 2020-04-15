---
title: カーソル ライブラリ操作 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2297e72aacad7ea91b7af934a47bebbc61f0686
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301619"
---
# <a name="cursor-library-operations"></a>カーソル ライブラリの操作
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC *2.x*ドライバを使用するアプリケーションが ODBC *3.x*カーソル ライブラリを呼び出す場合、ODBC *2.x*ドライバでサポートされていない ODBC *3.x*機能を使用できる可能性があります。 ただし、アプリケーション作成者は、これらの機能の使用方法に注意する必要があります。 ODBC *3.x*カーソル ライブラリを使用しても、ODBC *2.x*ドライバは ODBC *3.x*ドライバに変換されません。
