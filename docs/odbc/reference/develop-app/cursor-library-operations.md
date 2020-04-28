---
title: カーソルライブラリの操作 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301619"
---
# <a name="cursor-library-operations"></a>カーソル ライブラリの操作
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 *Odbc 2.x ドライバーを*使用しているアプリケーションが odbc *3. x*カーソルライブラリを呼び出すと *、odbc 2.x ドライバーで*サポートされていない odbc *3.x 機能を*アプリケーションで使用できる可能性があります。 ただし、アプリケーションの作成者は、これらの機能の使用方法を慎重に検討する必要があります。 Odbc *3. x*カーソルライブラリを使用しても、odbc 2.x*ドライバーは*odbc *3.x ドライバーに*はなりません。
