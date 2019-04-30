---
title: 標準のゲートウェイ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c70a558b065765dd9f8c0895345959e8aa22ebfe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232092"
---
# <a name="standard-gateway"></a>標準のゲートウェイ
A*ゲートウェイ*は別のように 1 つの DBMS を原因となるソフトウェアの一部です。 つまり、ゲートウェイ、プログラミング インターフェイス、SQL の文法とデータ ストリームを 1 つの DBMS のプロトコルとプログラミング インターフェイス、SQL の文法に変換されます受け取りデータ ストリームの非表示の DBMS のプロトコル。 たとえば、Microsoft® SQL Server™ を使用するアプリケーション データにアクセスできます DB2 マイクロ Decisionware DB2 ゲートウェイ; 経由この製品により、DB2 から SQL Server のようになります。 ゲートウェイを使用している場合は、ターゲット データベースごとに別のゲートウェイを書き込む必要があります。  
  
 ゲートウェイは、Dbms のアーキテクチャの違いによる制限は、標準化に適した候補では。 ただし、すべての Dbms プログラミング インターフェイスを標準化する場合は、SQL 文法、およびデータ ストリーム プロトコルが DBMS が、標準として選択するのには、1 つの DBMS のでしょうか。 確かに商用の DBMS ベンダーを競合企業の製品を標準化することに同意する可能性はありません。 その場合、標準的なプログラミング インターフェイス、SQL の文法とのデータ ストリーム プロトコルを開発すると、ゲートウェイは必要ありません。
