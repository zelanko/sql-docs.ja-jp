---
title: 製品サイクルの長さ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d235146ffe1b4699f0064c5772407bcf40ae962
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306195"
---
# <a name="length-of-the-product-cycle"></a>製品サイクルの長さ
相互運用性に関する最後の問題は時間です。 相互運用可能なアプリケーションの開発は、通常、相互運用できないアプリケーションを開発するよりも時間がかかります。 その理由は、アプリケーションが DBMS 機能をチェックし、異なる Dbms に対して同じタスクを異なる方法で実行し、一部の DBMS でサポートされている機能を回避し、他の DBMS ではサポートされていない機能を回避する必要があるためです。  
  
 開発時間に加えて、製品の寿命を考慮する必要があります。 DBMS から別の DBMS への移行時にデータを転送するアプリケーションなど、アプリケーションが一度だけ使用されるように設計されている場合、アプリケーションを相互運用可能にする意味はありません。 アプリケーションは一度使用され、破棄されます。  
  
 アプリケーションが長期間存在する場合は、相互運用可能なアプリケーションとして管理する方が簡単な場合があります。 これは、単一の DBMS をターゲットとして持つカスタム アプリケーションでも同様です。 その理由は、相互運用可能なコードがデータベース機能の限られたサブセットを使用するためです。 ドライバは、基になる DBMS に変更が加えられた場合でも、これらの機能を使用できるようにしておく必要があります。 したがって、相互運用可能なコードは、DBMS への変更に対処する負担をアプリケーション開発者からドライバー開発者に移す可能性があります。
