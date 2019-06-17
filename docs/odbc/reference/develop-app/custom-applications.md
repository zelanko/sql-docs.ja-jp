---
title: カスタム アプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ab470951162b5e4035c1253ed4ce425356ad8ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042528"
---
# <a name="custom-applications"></a>カスタム アプリケーション
通常、カスタム アプリケーションは、いくつかの Dbms の特定のタスクを実行します。 たとえば、アプリケーションが 1 つの DBMS のデータを取得し、レポートを生成またはいくつかの Dbms の間でデータを転送場合があります。 これらの Dbms が、アプリケーションが書き込まれる前に呼ばれ、アプリケーションの有効期間の経過と共に変化する可能性が低いことにはどのようなこれらのアプリケーションが共通します。  
  
 そのため、カスタム アプリケーションには、ほとんどまたはまったくない相互運用性が必要です。 アプリケーション開発者は、DBMS およびそれらのドライバーに直接コードごとに 1 つのドライバーを選択できます。 アプリケーションでは、それらのドライバーの機能を利用するドライバー固有のコードを安全に含めることができ、ODBC でサポートされていない機能を使用するネイティブのデータベース API の呼び出しを行うも可能性があります。  
  
 ほとんどのカスタム アプリケーションの主要な相互運用性の問題は、ターゲットの Dbms が、今後変更されるかどうか。 そうである場合、このプロセスが最初に相互運用性のコードを記述することで簡略化できます。 ただし、Dbms のような変更はほとんどありません、一般に、大量の作業が伴います。 このため、カスタム アプリケーションの開発者のことはほとんどありません選択機能を犠牲には、相互運用性を向上させる通常は Dbms を変更するときに、その機能を再コードを選択します。
