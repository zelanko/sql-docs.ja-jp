---
title: "DCOM を使用するクライアントでビジネス オブジェクトに登録する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e293eb58053259dd229656152094763ac31b48a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>DCOM を使用するクライアントでビジネス オブジェクトに登録します。
カスタム ビジネス オブジェクトは、クライアント側が DCOM 経由で使用できる識別子 (CLSID) にそのプログラム名 (ProgId) をマップできることを確認する必要があります。 このため、DCOM オブジェクトの ProgID 必要がありますでクライアント側のレジストリになり、サーバー側のビジネス オブジェクトのクラス ID にマップします。 その他のサポートされているプロトコル (HTTP、HTTPS、およびプロセス内)、これは必要ありません。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 たとえば、特定のクラス ID、たとえば、"{00112233-4455-6677-8899-00AABBCCDDEE}"mybobj サーバー側のビジネス オブジェクトを公開する場合を行います。 クライアント側のレジストリに次のエントリが追加されることを確認  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```



