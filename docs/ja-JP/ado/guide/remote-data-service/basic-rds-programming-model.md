---
title: プログラミング モデルの基本的な RDS |Microsoft ドキュメント
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
- RDS programming model [ADO]
ms.assetid: 0bdd236b-edff-4aac-94c3-93e1465ca6c5
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 453a06af95c04695c2502180015d2f24d0d28b50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="basic-rds-programming-model"></a>基本的な RDS プログラミング モデル
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 Rds は、次の環境に存在するアプリケーション: クライアント アプリケーションは、サーバーと必要な情報を返すために必要なパラメーターで実行するプログラムを指定します。 サーバーにアクセスできる、指定されたデータ ソースで呼び出されたプログラムは、情報を取得します、必要に応じて、データを処理および簡単に使用できる形式でクライアント アプリケーションに結果として得られる情報を返します。 RDS の次の一連の操作を実行するための手段を提供します。  
  
-   サーバーで、呼び出されるプログラムを指定し、クライアントから参照する方法を取得します。 (この参照と呼ぶことが、*プロキシ*です。 これは、リモート サーバーのプログラムを表します。 クライアント アプリケーションは""プロキシよう呼び出すローカルのプログラムが、リモート サーバーのプログラムを実際に呼び出します。)  
  
-   サーバーのプログラムを起動します。 データ ソースおよび発行するコマンドを識別するサーバーのプログラムにパラメーターを渡します。 (サーバー プログラム実際に ADO を使用して、データ ソースにアクセスできるようにします。 ADO が指定されたパラメーターのいずれかの接続を作成し、他のパラメーターで指定されたコマンドを発行します。)  
  
-   サーバーのプログラムを取得、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)データ ソースからのオブジェクト。 必要に応じて、**レコード セット**オブジェクトは、サーバーで処理します。  
  
-   サーバーを返します、最終的な**レコード セット**をクライアント アプリケーションのオブジェクト。  
  
-   クライアントで、 **Recordset**オブジェクトがビジュアル コントロールで簡単に使用できるフォームに配置します。  
  
-   変更を加える、 **Recordset**オブジェクトは、データ ソースを更新するために使用されるサーバー プログラムに送信します。  
  
 このプログラミング モデルには、便利な機能が含まれています。 データ ソースにアクセスする複雑なサーバーのプログラムを必要としないし、必要な接続とコマンド パラメーターを提供する場合は、自動的に場合は、単純な場合、既定のサーバー プログラムで指定されたデータを取得します。  
  
 複雑な処理を必要がある場合は、独自のカスタム サーバー プログラムを指定できます。 たとえば、カスタム サーバー プログラムには、ADO の破棄された時点の全機能があるため、いくつかの異なるデータ ソースに接続、複雑な方法でそのデータを組み合わせる、クライアント アプリケーションに簡単で処理された結果を返すおよびでした。  
  
 最後に場合は、必要では、ADO サポート既定のサーバー プログラムの動作をカスタマイズします。  
  
## <a name="see-also"></a>参照  
 [RDS プログラミング モデルの詳細](../../../ado/guide/remote-data-service/rds-programming-model-in-detail.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


