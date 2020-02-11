---
title: ExtendedAnsiSQL | の設定Microsoft Docs
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
ms.openlocfilehash: 330b55ef2d4fee090c453990d3fe75e6e2dacb6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063600"
---
# <a name="setting-extendedansisql"></a>ExtendedAnsiSQL の設定
ExtendedAnsiSQL 属性を追加することで、接続文字列内の属性を制御できます。  
  
|値|[説明]|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (既定値)|この設定では、新しい機能は有効になりません。|  
|ExtendedAnsiSQL = 1|この設定により、新しい機能が有効になります。|  
  
 属性は、コントロールパネルで DSN を構成するときに、 **[詳細オプション**] ダイアログボックスで dsn で設定することもできます。  
  
 属性を0に設定すると、新しい機能が無効になります。1に設定すると、新しい機能が有効になります。  
  
 属性は、SQLSetConnectAttr () を使用して設定することもできます。 属性値は65501で、前の表に記載されているように、SQLINTEGER 値が1または0に設定されています。 接続の前または後に呼び出すことができますが、キャッシュされた接続属性と接続文字列をドライバーが処理する順序によって、接続後に呼び出す方が適切です。
