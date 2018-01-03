---
title: "コンポーネント サービスでビジネス オブジェクトを実行している |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 162f91a88f9e1b7fcd96ec5fa637a608b87b0921
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="running-business-objects-in-component-services"></a>コンポーネント サービスでビジネス オブジェクトを実行しています。
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 ビジネス オブジェクトには、実行可能ファイル (.exe) またはダイナミック リンク ライブラリ (.dll) を指定できます。 ビジネス オブジェクトの実行に使用する構成は、オブジェクトは、.dll または .exe ファイルかどうかによって異なります。  
  
-   .Exe ファイルとして作成されたビジネス オブジェクトは、DCOM を介して呼び出すことができます。 インターネット インフォメーション サービス (IIS) を介してこれらのビジネス オブジェクトを使用する場合があります、クライアントのパフォーマンスが低下するデータの追加のマーシャ リングします。  
  
-   .Dll ファイルを IIS を使用するように作成されたビジネス オブジェクトおよび HTTP でもします。 こともできます DCOM コンポーネント サービス、または Microsoft Transaction Server を介してのみを介して Windows NT を使用している場合。 ビジネス オブジェクトの Dll は、IIS からそれらにアクセスする IIS サーバー コンピューターに登録する必要があります。 DCOM 上で実行する DLL を構成する方法についてを参照してください、 [DCOM で実行するように、DLL を有効にする](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md)です。  
  
> [!NOTE]
>  使用して、中間層ビジネス オブジェクトがコンポーネント サービスのコンポーネントとして実装すると**GetObjectContext**、 **SetComplete**、および**SetAbort**、ビジネスオブジェクトは、コンポーネント サービス (または Windows NT を使用している場合は MTS) を使用できるコンテキスト オブジェクトは、複数のクライアント呼び出しでの状態を維持します。 このシナリオでは、DCOM で、信頼されたクライアントとイントラネット内のサーバー間では、通常実装を持つ可能性があります。 ここで、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクトおよび[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)クライアント側のメソッドは、トランザクション コンテキストのオブジェクトに置き換え、 **CreateInstance** 用意されているメソッド**ITransactionContext**インターフェイスし、コンポーネント サービスによって実装されます。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)


