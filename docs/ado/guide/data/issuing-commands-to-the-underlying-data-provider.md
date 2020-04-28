---
title: 基になる Data Provider | にコマンドを発行するMicrosoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02a861daa78b798c1b19b5fc2607cfcaf0ce5968
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924946"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>基になるデータ プロバイダーにコマンドを発行する
図形で始まらないコマンドは、データプロバイダーに渡されます。 これは、"SHAPE {provider command}" という形式で shape コマンドを発行することと同じです。 これらのコマンドでは、**レコードセット**を生成する必要はあり*ません*。 たとえば、データプロバイダーが DROP TABLE をサポートしていると仮定した場合、"SHAPE {DROP TABLE MyTable} は完全に有効な shape コマンドです。  
  
 この機能により、通常のプロバイダーコマンドとシェイプコマンドの両方で同じ接続とトランザクションを共有できます。  
  
## <a name="see-also"></a>参照  
 [データシェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [仮形の文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
