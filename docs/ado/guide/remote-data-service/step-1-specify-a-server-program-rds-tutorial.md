---
title: '手順 1: サーバー プログラム (RDS チュートリアル) を指定する |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5583f9b2c5093859e9bb5d3fd0eb9444828cb4bc
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558299"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>手順 1: サーバー プログラムを指定する (RDS チュートリアル)
最も一般的な場合に、使用、 [rds.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクト[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)既定のサーバー プログラムを指定するメソッド[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)、または独自のカスタム サーバー プログラム (ビジネス オブジェクト)。 サーバーのプログラムが、サーバーとサーバーのプログラムへの参照でインスタンス化または*プロキシ*が返されます。  
  
 このチュートリアルでは、既定のサーバー プログラムを使用します。  
  
```vb
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="see-also"></a>参照  
 [手順 2: サーバー プログラム (RDS チュートリアル) を起動します。](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
