---
title: モジュールとプロローグ (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bcedc4f9e018a60d6a80f91a9b1d65b791abd08b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="modules-and-prologs-xquery"></a>モジュールとプロローグ (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)する一連の名前空間の宣言です。 プロローグで名前空間の宣言を使用すると、名前空間のバインドにプレフィックスを指定して、クエリ本文でそのプレフィックスを使用できます。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 次の XQuery 仕様は、この実装ではサポートされません。  
  
-   モジュール宣言 (`version`)  
  
-   モジュール宣言 (`module namespace`)  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   既定の照合順序の宣言 (`declare default collation`)  
  
-   基本 URI 宣言 (`declare base-uri`)  
  
-   構築宣言 (`declare construction`)  
  
-   既定の順序の宣言 (`declare ordering`)  
  
-   スキーマのインポート (`import schema namespace`)  
  
-   モジュールのインポート (`import module`)  
  
-   プロローグでの変数宣言 (`declare variable`)  
  
-   関数宣言 (`declare function`)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)  
 XQuery プロローグをについて説明します。  
  
## <a name="see-also"></a>参照  
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
