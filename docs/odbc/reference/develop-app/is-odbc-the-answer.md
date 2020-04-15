---
title: ODBC が正解ですか? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], ODBC
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3716acbcc1b8ea648b5edc03e277983936da557
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288093"
---
# <a name="is-odbc-the-answer"></a>ODBC が正解ですか?
相互運用性の問題を掘り下げる前に、次の質問を検討してください: アプリケーションは、ODBC をまったく使用する必要がありますか? これは ODBC のガイドで尋ねる奇妙な質問に思えるかもしれませんが、実際には正当なものです。 ODBC は、ネイティブ データベース API を完全に置き換えるように設計されたものではなく、すべての状況でデータベース アクセスを提供するように設計されていません。 データベースに共通のインターフェイスを提供するように設計されており、アプリケーション プログラマが複数のデータベースへのリンクを学習して維持する必要がなくなります。  
  
 カスタム アプリケーションは、ネイティブ データベース API の主要な候補です。 主な理由は、カスタム アプリケーションは、多くの場合、1 つの DBMS で動作し、相互運用可能である必要がないためです。 ネイティブ データベース API は、特定の DBMS の機能を公開する ODBC よりも優れた処理を行い、ODBC によって公開されない機能を公開する場合があります。 さらに、カスタム アプリケーションの開発者は、通常、DBMS のネイティブ データベース API に精通しているため、ODBC を学習する必要はほとんどありません。 ただし、一部の DBMS では、ODBC がネイティブ データベース API であることに注意してください。  
  
 では、どのアプリケーションが ODBC の候補となるのでしょうか。 最も適した方法は、複数の DBMS で動作するアプリケーションです。 これには、事実上すべての汎用アプリケーションと垂直アプリケーションが含まれます。 また、多数のカスタム アプリケーションも含まれています。 たとえば、複数の異なる Dbms を使用するカスタム アプリケーションは、複数のネイティブ API を使用するよりも、ODBC を使用して書き込む方がはるかに簡単で、よりクリーンです。 また、ODBC で作成されたカスタム アプリケーションは、企業が DBMS から別の DBMS に移行したり、異なる DBMS に対して同じアプリケーションをデプロイしたりすると、移行がはるかに簡単になります。
