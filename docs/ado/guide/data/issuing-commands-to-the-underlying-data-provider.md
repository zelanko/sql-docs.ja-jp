---
title: 基になるデータ プロバイダーにコマンドを発行する |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a2e18440c651a65da820cf2f2d51b00ae98e92d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271951"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>基になるデータ プロバイダーにコマンドを発行します。
図形で始まっていない任意のコマンドは、データ プロバイダーにを介して渡されます。 これは、"SHAPE {プロバイダー コマンド}"の形式で図形コマンドの発行に相当します。 これらのコマンドは*いない*を生成する必要がある、**レコード セット**です。 たとえば、"図形 {ドロップ テーブル MyTable} は完全に有効な図形コマンドでは、データ プロバイダーは、DROP TABLE をサポートするいると仮定した場合です。  
  
 この機能は、通常のプロバイダー コマンドと同じ接続とトランザクションを共有する図形コマンドの両方をによりします。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
