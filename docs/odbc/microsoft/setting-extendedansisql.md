---
title: ExtendedAnsiSQL の設定 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9b8999e229e8a6ed4804b2f06a4072d139ae93a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159367"
---
# <a name="setting-extendedansisql"></a>ExtendedAnsiSQL の設定
ExtendedAnsiSQL 属性を追加することで、接続文字列で、属性を制御できます。  
  
|値|説明|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (既定)|この設定は、新しい機能を有効になりません。|  
|ExtendedAnsiSQL=1|この設定により、新機能です。|  
  
 経由の DSN で属性を設定することも、**オプションの高度な** ダイアログ ボックスのコントロール パネルを使用した DSN を構成するときにします。  
  
 0 にする属性を設定する; の新機能により、新機能を 1 に設定します。  
  
 SQLSetConnectAttr() を使用して、属性を設定することもできます。 属性の値は 65501 し、前の表に記載されているが、1 または 0 の SQLINTEGER 値に設定します。 前に、または接続した後、呼び出すことができますが、接続属性および接続文字列、ドライバー プロセスがキャッシュされる順序が原因で接続した後に呼び出すことをお勧めします。
