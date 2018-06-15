---
title: カスタム アプリケーション |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9475bc17948e2146493cade0f884cac8885eea62
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908387"
---
# <a name="custom-applications"></a>カスタム アプリケーション
通常、カスタム アプリケーションは、いくつかの Dbms の特定のタスクを実行します。 アプリケーション可能性があります単一 DBMS からデータを取得し、レポートを生成など、いくつかの Dbms の間でデータを転送可能性があります。 どのようなこれらのアプリケーションが共通では、これらの Dbms が、アプリケーションが書き込まれる前に呼ばれ、アプリケーションの有効期間の経過と共に変化する可能性が低いことです。  
  
 したがって、カスタム アプリケーションには、ほとんどまたはまったくない相互運用性が必要です。 アプリケーション開発者は、各 DBMS およびそれらのドライバーを直接コードを 1 つのドライバーを選択できます。 アプリケーションでは、それらのドライバーの機能を利用するドライバー固有のコードを安全に含めることができ、ODBC でサポートされていない機能を使用して、ネイティブ データベース API 呼び出しを行うも可能性があります。  
  
 ほとんどのカスタム アプリケーションの主要な相互運用性の問題は、ターゲットの Dbms が、今後変更されるかどうかです。 場合は、最初に相互運用コードを記述してこのプロセスを簡略化できます。 ただし、このような変更の Dbms はまれであり大量の作業を一般に任せます。 このため、カスタム アプリケーションの開発者ことはほとんどありません選択機能を犠牲にして相互運用性を向上させるこれらは通常を Dbms を変更するときに、その機能を書き直すを選択します。
