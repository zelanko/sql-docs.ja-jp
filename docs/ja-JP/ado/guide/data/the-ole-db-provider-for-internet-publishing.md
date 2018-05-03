---
title: インターネットへの発行の OLE DB Provider |Microsoft ドキュメント
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
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 908160d594df0c24b45960e30a1d50cbebed6416
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>インターネットへの発行用の OLE DB プロバイダー
ADO[レコード](../../../ado/reference/ado-api/record-object-ado.md)と[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトで使える Microsoft OLE DB Provider for Internet Publishing (インターネット発行プロバイダー) にアクセスして、リソースを操作する Web フォルダーやファイルなどMicrosoft によって処理されます。 ADO のソースを指定することができます、**レコード**、**ストリーム**、または[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) URL であります。 ことができますし、アップロード、ダウンロード、移動、コピー、および、リソースを削除またはリソースのプロパティを直接操作します。  
  
 使用するコード例**レコード**と**ストリーム**公開インターネット プロバイダーは、次を参照してください。、[インターネット発行シナリオ](../../../ado/guide/data/internet-publishing-scenario.md)です。  
  
 インターネット、パブリッシング用プロバイダーは、Microsoft Windows 2000 と共にインストールされます。 以前のバージョンのインターネット発行プロバイダーも Microsoft Office 2000 と Microsoft Internet Explorer 5.0 以降で使用できます。  
  
 ストアには、ADO プロバイダーに接続する、インターネット発行の 3 つの方法があります。  
  
-   指定"URL ="接続文字列にします。 以下に例を示します。  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   指定の Msdaipp.dso、*プロバイダー*接続文字列のキーワードです。 以下に例を示します。  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   指定の Msdaipp.dso、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)のプロパティ、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。 以下に例を示します。  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Msdaipp.dso が、プロバイダーは、のいずれかの値として明示的に指定されている場合、*プロバイダー*接続文字列キーワード、または**プロバイダー**プロパティは使用できません"URL ="接続文字列にします。 この場合、エラーが発生します。 代わりに、単に URL を指定前に示したようです。  
  
 インターネット、パブリッシング用プロバイダーの詳細については、次を参照してください[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)、または使用する送信元アプリケーションで提供されるプロバイダーのドキュメントの OLE DB プロバイダー。Internet Publishing がインストールされた: Windows 2000、Office 2000、または Internet Explorer 5.0 です。
