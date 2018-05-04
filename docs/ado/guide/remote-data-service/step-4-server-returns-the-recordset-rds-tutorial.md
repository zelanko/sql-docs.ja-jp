---
title: '手順 4: サーバーは、レコード セット (RDS チュートリアル) を返します |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7307eeef65ce29f02d864396100134a8082a754d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>手順 4: サーバーは、レコード セット (RDS チュートリアル) を返します
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 RDS に取得した変換**レコード セット**クライアントに送信できる形式にオブジェクト (つまり、*マーシャ リング*、**レコード セット**)。 送信方法と、変換の正確な形式は、サーバーがインターネットまたはイントラネット、ローカル エリア ネットワーク上であるかダイナミック リンク ライブラリに依存します。 ただし、この詳細重要ではありません。関心のある情報がその RDS すべてを送信、 **Recordset**クライアントに返送します。  
  
 クライアント側で、 **Recordset**オブジェクトが返され、ローカル変数に代入します。  
  
```  
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>参照  
 [手順 5: DataControl が行われた使用可能な (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
