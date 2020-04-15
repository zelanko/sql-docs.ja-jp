---
title: カスタムアプリケーション |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df00a748ee4d5e3a63b32c95449417a1057b58e1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305283"
---
# <a name="custom-applications"></a>カスタム アプリケーション
カスタム アプリケーションでは、一般的に、いくつかの Dbms に対して特定のタスクを実行します。 たとえば、アプリケーションが 1 つの DBMS からデータを取得してレポートを生成したり、複数の DBMS 間でデータを転送したりすることがあります。 これらのアプリケーションに共通しているのは、これらの DBMS はアプリケーションが作成される前に認識されており、アプリケーションの有効期間にわたって変更される可能性が低いということです。  
  
 したがって、カスタム アプリケーションは相互運用性をほとんど必要としません。 アプリケーション開発者は、DBMS ごとに 1 つのドライバーを選択し、それらのドライバーに直接コードを記述できます。 アプリケーションは、ドライバー固有のコードを安全に含めることで、これらのドライバーの機能を利用でき、ネイティブ データベース API を呼び出して ODBC でサポートされていない機能を使用する場合もあります。  
  
 ほとんどのカスタム アプリケーションでの相互運用性の大きな懸念は、ターゲット DBMS が将来変更されるかどうかです。 その場合、このプロセスは、より相互運用可能なコードを記述することで単純化できます。 しかし、このような DBMS の変更はまれであり、一般的に大量の作業が必要です。 このため、カスタム アプリケーションの開発者が、機能を犠牲にして相互運用性を高める選択をすることはめったにありません。通常、DBMS を変更するときに、その機能を再コードすることを選択します。
