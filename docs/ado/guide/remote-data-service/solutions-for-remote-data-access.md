---
title: "リモート データ アクセス用のソリューション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS [ADO]
ms.assetid: d311cc67-7db7-4c43-9590-d465564695e4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9030af4a02555aac77428ba9490ee72e87b93681
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="solutions-for-remote-data-access"></a>リモート データ アクセス用のソリューション
## <a name="the-issue"></a>問題  
 ADO を使用すると、アプリを直接へのアクセスおよび (2 層システムとも呼ばれます) のデータ ソースを変更します。 たとえば、データを含むデータ ソースへの接続がある場合内にある直接接続 2 層システムです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 ただし、Microsoft® インターネット インフォメーション サービス (IIS) などの中間層でないデータ ソースに直接アクセスすることがあります。 この方法は、3 層システムと呼ばれます。 IIS は、インターネットまたはイントラネットの間で、リモートまたはサーバー、プログラムを起動するか、クライアント、アプリケーションの効率的な方法を提供するクライアント/サーバー システムです。 サーバー プログラムは、データ ソースにアクセスし、必要に応じて取得したデータを処理します。  
  
 たとえば、イントラネットの Web ページには、Microsoft® Visual Basic Scripting Edition (VBScript) を IIS に接続するで記述されたアプリケーションが含まれています。 IIS で、さらに、実際のデータ ソースに接続、データを取得、何らかの方法で処理、およびアプリケーションに処理済みの情報を返します。  
  
 この例では、アプリケーションに直接接続、データ ソースです。IIS は次のとおりでした。 IIS ADO を使用してデータにアクセスします。  
  
> [!NOTE]
>  クライアント/サーバー アプリケーションは、インターネットまたはイントラネットに基づいて作成する必要はありません (つまり、Web ベース) — だけのローカル エリア ネットワーク上のコンパイル済みのプログラムで構成されている可能性があります。 ただし、通常の場合は、Web ベース アプリケーションです。  
  
 グリッド、チェック ボックス、または一覧など、いくつかのビジュアル コントロールは、返される情報を使用する場合があります、ためビジュアル コントロールによって返される情報を簡単に使用する必要があります。  
  
 シンプルで効率的なアプリケーション プログラミング インターフェイスをサポートして、3 層システムに関する情報を返しますとして簡単に取得されていた場合、2 層システムを必要とします。 リモート データ サービス (RDS) は、このインターフェイスです。  
  
## <a name="the-solution"></a>解決策  
 RDS プログラミング モデルを定義する — にアクセスし、データ ソースを更新するために必要な活動のシーケンス — 中継ぎ局であり、インターネット インフォメーション サービス (IIS) などを使用してデータにアクセスするためにします。 プログラミング モデルは、RDS の全体の機能をまとめたもの。  
  
## <a name="see-also"></a>参照  
 [基本的な RDS プログラミング モデル](../../../ado/guide/remote-data-service/basic-rds-programming-model.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



