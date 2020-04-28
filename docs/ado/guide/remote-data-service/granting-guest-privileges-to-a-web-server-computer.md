---
title: Web サーバーコンピューターにゲスト特権を付与する |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bddf6ce0bbfb78435118ef3d87303a94c792c96d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922643"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Web サーバー コンピューターへのゲスト特権の付与
RDS を使用するには、匿名 Web サーバーアカウント (IUSR_*ComputerName*) を web サーバーコンピューターの Guests ローカルグループに追加する必要があります。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Web サーバーコンピューターにゲスト特権を付与するには  
  
1.  Microsoft Windows 2000 Server コンピューターで、[**スタート**] をクリックし、[**プログラム**]、[**管理ツール**] の順にポイントし、[**コンピューターの管理**] をクリックします。  
  
2.  コンソールツリーの [**ローカルユーザーとグループ**] で、[**グループ**] をクリックします。  
  
3.  [ **Guests** ] ローカルグループを選択します。 [**操作**] メニューの [**プロパティ**] をクリックします。  
  
4.  [ **Guests のプロパティ**] ダイアログボックスで、[**追加**] をクリックします。  
  
5.  匿名 Web サーバーアカウントが **[ユーザーまたはグループの選択**] ダイアログボックスの一覧に表示されない場合は、その名前 (IUSR_*ComputerName*) を下の空白のボックスに入力し、[**追加**] をクリックします。  
  
6.  **[OK]** をクリックします。


