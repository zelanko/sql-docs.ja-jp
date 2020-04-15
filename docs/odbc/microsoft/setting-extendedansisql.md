---
title: 拡張を設定する|マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b5c2e4ed4d8bd64d02fb6a62861db832f6b0898
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300802"
---
# <a name="setting-extendedansisql"></a>ExtendedAnsiSQL の設定
この属性は、ExtendedAnsiSQL 属性を追加することで、接続文字列で制御できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|拡張アンシSQL=0 (デフォルト)|この設定では、新しい機能は有効になっていません。|  
|拡張アンシSQL=1|この設定により、新機能が有効になります。|  
  
 コントロール パネルから DSN を構成するときに、[**詳細オプション]** ダイアログ ボックスを使用して、DSN で属性を設定することもできます。  
  
 属性を 0 に設定すると、新しい機能は無効になります。1 に設定すると、新機能が有効になります。  
  
 この属性は、SQLSetConnectAttr() を使用して設定することもできます。 属性値は 65501 で、前の表に示されているように、SQLINTEGER 値 1 または 0 に設定されます。 これは接続の前または後に呼び出すことができますが、ドライバーがキャッシュされた接続属性と接続文字列を処理する順序のために接続後に呼び出すことをおやめください。
