---
title: Web サーバー コンピューターへのゲストの特権の付与 |Microsoft ドキュメント
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
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7128286a68184f89ecc3da7914f7a1787378335b
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Web サーバー コンピューターへのゲストの特権の付与
匿名の Web サーバー アカウント (iusr _*ComputerName*) RDS を使うため、ゲストをローカル Web サーバー コンピューターのグループに追加する必要があります  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Web サーバー コンピューターに guest の権限を付与するには  
  
1.  Microsoft Windows 2000 Server コンピューターでは、をクリックして**開始**、 をポイント**プログラム**、 をポイント**管理ツール**、クリックして**コンピューター管理**です。  
  
2.  コンソール ツリーで**ローカル ユーザーとグループ**をクリックして**グループ**です。  
  
3.  選択、**ゲスト**ローカル グループです。 **アクション**] メニューの [選択**プロパティ**です。  
  
4.  **ゲスト プロパティ**ダイアログ ボックスで、をクリックして**追加**です。  
  
5.  一覧で、匿名の Web サーバー アカウントが表示されないかどうか、 **[ユーザーまたはグループ**] ダイアログ ボックスで、その名前を入力 (iusr _*ComputerName*) クリックして下の空のボックスに**追加**.  
  
6.  **[OK]**をクリックします。


