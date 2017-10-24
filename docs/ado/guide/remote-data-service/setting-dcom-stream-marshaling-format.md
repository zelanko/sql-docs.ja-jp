---
title: "DCOM のストリームのマーシャ リング形式を設定 |Microsoft ドキュメント"
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
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: abc77e2e56ec8251e158121ca8bb6083641d4cb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setting-dcom-stream-marshaling-format"></a>DCOM のストリームのマーシャ リング形式を設定
RDS 1.5 以前のコンポーネントを使用してクライアント コンピューターは、RDS 2.0 またはそれ以降のコンポーネントを使用するサーバーと互換性がありません。 RDS 2.0 またはそれ以降のサポートが効率的に転送する、基になるプロトコルとして DCOM を使用して、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 場合は、クライアントには、RDS 1.5 以前のコンポーネントが実行されて、(RDS 1.0 と呼ばれます) 前の RDS サポートまたは新しい RDS サポート (RDS 2.0 またはそれ以降) を使用するようにサーバーを設定できます。 次のレジストリ エントリのいずれかを設定します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -または-  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```



