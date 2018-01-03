---
title: "設定 ExtendedAnsiSQL |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d263d57d9fecbcb03f737dc73472452367900a47
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="setting-extendedansisql"></a>ExtendedAnsiSQL の設定
属性は、ExtendedAnsiSQL 属性を追加することで、接続文字列に制御できます。  
  
|値|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (既定値)|この設定には、新しい機能が有効にしません。|  
|ExtendedAnsiSQL = 1|この設定は、新しい機能を有効します。|  
  
 属性を使用して、DSN に設定することもできます、**オプションの高度な** ダイアログ ボックスのコントロール パネルを使用して、DSN を構成するときにします。  
  
 属性を設定する 0 に、新しい機能です。新機能を 1 に設定できます。  
  
 SQLSetConnectAttr() を使用して、属性を設定することもできます。 属性の値は、65501 でに設定されている SQLINTEGER 値 1 または 0 の場合のように、前の表に記載されています。 前に、または接続した後、呼び出すことができますが、ドライバーのプロセスがキャッシュされている接続属性および接続文字列の順序のための接続後に呼び出すことをお勧めします。
