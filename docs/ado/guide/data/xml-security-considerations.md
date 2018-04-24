---
title: XML のセキュリティに関する考慮事項 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cbfee8717021fbc1eb621591987ee63ab54362e6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="xml-security-considerations"></a>XML のセキュリティに関する考慮事項
ADO を保存し、レコード セット オブジェクトの Open メソッドは、Internet Explorer で実行するセーフである操作は考慮されません。 したがって、アプリケーションまたはブラウザーでホストされるコントロールで実行されているスクリプト コードでこれらのメソッドを使用している場合、ブラウザーのセキュリティ構成すると、その動作に影響があります。  
  
 Internet Explorer 5 は、既定のインターネット ゾーンでこのような操作に対するセキュリティ制限を提供します。 その構成では、レコード セットはクライアントのローカル ファイル システムへのアクセスを行うまたはページのダウンロード元サーバーのドメイン外の任意のデータ ソースにアクセスできません。 具体的には、ブラウザー ホスト内の実行中、レコード セットに保存できますバックアップ ファイル、ページのダウンロード元となる、同じサーバー上にある場合にのみです。 同様に、ページがダウンロードされた、同じサーバーにファイルがある場合にのみファイルから読み込むことにより、レコード セットを開くことができます。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
