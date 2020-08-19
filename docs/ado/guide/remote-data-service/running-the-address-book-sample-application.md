---
description: アドレス帳のサンプル アプリケーションの実行
title: アドレス帳サンプルアプリケーションを実行する |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fddb0d0fb2d7a49c7b9983c03157922862f5d96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452004"
---
# <a name="running-the-address-book-sample-application"></a>アドレス帳のサンプル アプリケーションの実行
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 アドレス帳アプリケーションを実行するには、次の手順に従います。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
### <a name="to-run-this-application"></a>このアプリケーションを実行するには  
  
1.  Microsoft SQL Server が実行されていることを確認します。 [ **スタート**] をクリックし、[ **プログラム**]、[ **Microsoft SQL Server 7.0**] の順にポイントし、[ **Service Manager**] をクリックします。 白の円に緑色の矢印がある場合は、SQL Server が実行されています。 表示されていない場合は (白い丸の中に赤色の四角形が表示されます)、[ **開始/続行**] をクリックします。  
  
2.  Microsoft Internet Explorer 4.0 以降で、次のアドレスを入力します。  
  
     **https://** *web*サーバー **/RDS/AddressBook/AddrBook.asp**  
  
     ここで、 *webserver* は、RDS サーバーコンポーネントがインストールされている Web サーバーの名前です。  
  
3.  その後、アドレス帳のサンプルアプリケーションでさまざまなシナリオを試すことができます。たとえば、電子メール名に基づいて個人を検索したり、"プログラムマネージャー" というタイトルのすべてのユーザーを一覧表示したり、既存のレコードを編集したりします。 [ **検索** ] をクリックすると、使用可能なすべての名前がデータグリッドに表示されます。  
  
## <a name="see-also"></a>参照  
 [アドレス帳のデータ バインディング オブジェクト](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)




