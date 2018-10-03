---
title: カーソル ライブラリの操作 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e3fcaf9c83c2613a1dc2df499f11c7df2570ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692400"
---
# <a name="cursor-library-operations"></a>カーソル ライブラリの操作
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 場合、ODBC 2 アプリケーション *.x*ドライバーは ODBC 3 への呼び出しを行います *。x*カーソル ライブラリでは、アプリケーションが ODBC 3 を使用することがあります *。x* ODBC 2 でサポートされていない機能 *.x*ドライバー。 アプリケーションの作成者は、これらの機能の使い方、ただし、注意でしなければなりません。 ODBC 3 を使用します。*x*カーソル ライブラリは、ODBC 2 には行いません *.x* 、ODBC 3 にドライバー *。x*ドライバー。
