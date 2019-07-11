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
ms.openlocfilehash: 748d917ad060609d40e40a24e5669cff37188691
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792665"
---
# <a name="cursor-library-operations"></a>カーソル ライブラリの操作
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 場合、ODBC を使用するアプリケーション*2.x*ドライバーは、odbc 呼び出しを行う*3.x*カーソル ライブラリでは、アプリケーションが ODBC を使用することがあります*3.x*れていない機能ODBC でサポートされている*2.x*ドライバー。 アプリケーションの作成者は、これらの機能の使い方、ただし、注意でしなければなりません。 ODBC の使用*3.x*カーソル ライブラリは、ODBC には行いません*2.x*に ODBC ドライバー *3.x*ドライバー。
