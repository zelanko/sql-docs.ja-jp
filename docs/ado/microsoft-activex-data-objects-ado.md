---
title: "Microsoft ActiveX Data Objects (ADO) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.prod: sql-non-specified
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, about
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 28fa2c279cfd7964d8516514a3caed129e335692
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-activex-data-objects-ado"></a>Microsoft ActiveX Data Objects (ADO)

ADO は、SQL Server に接続する C++ プログラムで使用されます。 もちろん、でも使用、クラウドで Azure SQL Database に接続できます。

この記事では、各セクションでは、ADO のコンポーネントについて説明します。

> [!NOTE]
> ADO.NET が ADO と異なります。 ADO.NET、およびその他の多くの SQL 接続ドライバーおよびその言語は開始位置として説明[SQL Server ドライバー](../connect/sql-connection-libraries.md)です。

  
## <a name="ado"></a>ADO (ADO)  
 Microsoft ActiveX データ オブジェクト (ADO) では、クライアント アプリケーションにアクセスして、さまざまな OLE DB プロバイダー経由のソースからデータを操作が有効にします。 その主な利点は、使いやすさ、高速、メモリ不足のオーバーヘッドと少数のディスク使用量です。 ADO では、クライアント/サーバーおよび Web ベースのアプリケーションを構築する主な機能をサポートしています。  
  
## <a name="ado-md"></a>ADO MD (ADO MD)  
 Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) は、Microsoft Visual Basic、および Microsoft Visual C などの言語から多次元データへ簡単にアクセスを提供します。 ADO MD CubeDef およびセルセット オブジェクトなどの多次元データに固有のオブジェクトを含める Microsoft ActiveX データ オブジェクト (ADO) を拡張します。 ADO md マルチ ディメンション スキーマの参照、キューブを照会でき、結果を取得できます。  
  
 ADO と同様には、ADO MD は、データにアクセスするために、基になる OLE DB プロバイダーを使用します。 ADO MD を使用するには、プロバイダーは、OLE DB for OLAP 仕様で定義されている多次元データ プロバイダー (MDP) をする必要があります。 Mdp 表形式のデータ プロバイダー (Tdp) ではなくマルチ ディメンションのビューでデータを示すでデータの表形式ビュー。 詳細については、特定の構文と、プロバイダーでサポートされている動作 OLAP OLE DB プロバイダーのマニュアルを参照してください。  
  
## <a name="rds"></a>RDS  
 リモート データ サービス (RDS) は、ADO を使用するをサーバーからデータをクライアント アプリケーションまたは Web ページに移動、クライアントでは、データを操作して、1 回のラウンド トリップでサーバーに更新プログラムを返しての機能です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="adox"></a>ADOX  
 データ定義言語およびセキュリティ (ADOX) の Microsoft の ActiveX データ オブジェクトの拡張は、ADO オブジェクトおよびプログラミング モデルの拡張機能です。 ADOX には、スキーマの作成と変更、およびセキュリティに対してオブジェクトが含まれています。 スキーマ操作オブジェクト ベースのアプローチであるために、さまざまなデータに対してネイティブの構文ではその違いに関係なくソースは機能するコードを記述できます。  
  
 ADOX は、コア ADO オブジェクト コンパニオン ライブラリです。 これは、作成、変更、およびテーブルおよびプロシージャなどのスキーマ オブジェクトを削除するオブジェクトを公開します。 ユーザーとグループの管理とを与えるオブジェクトに対する権限を取り消すセキュリティ オブジェクトも含まれています。  
  
## <a name="documentation"></a>ドキュメント  
 [ADO セキュリティのデザインに関する問題](../ado/guide/ado-security-design-issues.md)  
  
 [ADO プログラマ ガイド](../ado/guide/ado-programmer-s-guide.md)  
  
 ADO、RDS、ADO MD ADOX を使用して概要です。  
  
 [ADO プログラマーズ リファレンス](../ado/reference/ado-programmer-s-reference.md)  
  
 ADO のドキュメントのこのセクションには、各 ADO、RDS、ADO MD と ADOX オブジェクト、コレクション、プロパティ、動的なプロパティ、メソッド、イベント、および列挙体についてのトピックが含まれています。  
  
 [ADO の用語集](../ado/ado-glossary.md)  
  
## <a name="support"></a>サポート  
 無料の ADO 問題がある役立ちますが、ADO パブリック ニュースグループに投稿してください。 このニュースグループは、他の経験を積んだ ADO 開発者と ADO をカバーするマイクロソフト製品サポート サービス (PSS) のサポート担当者によって監視されます。  
  
 サポート オプションの詳細については、Microsoft ヘルプとサポート Web サイトで参照できます。



