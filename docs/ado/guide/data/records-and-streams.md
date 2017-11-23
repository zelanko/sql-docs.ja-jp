---
title: "レコードとストリーム |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streams [ADO]
- streams [ADO], about streams
- records [ADO]
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cfe5f8e48eb88233949102e988f3a2296cf373b4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="records-and-streams"></a>レコードとストリーム
ADO は、現在、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト リレーショナル データベースなどのデータ ソース内の情報にアクセスする主な手段として。 ただし、一部のプロバイダーのサポート、[レコード](../../../ado/reference/ado-api/record-object-ado.md)と[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)のプロバイダーからのデータを操作できるオブジェクトの代替または補完としてオブジェクト。 特性について**レコード**動作、プロバイダーのマニュアルを参照してください。  
  
## <a name="records"></a>[レコード]  
 **レコード**のオブジェクトが本質的に、1 行を機能**Recordset**s。 ただし、**レコード**に比較機能が制限**レコード セット**さまざまなプロパティとメソッドがあるとします。内のデータ ソース、**レコード**オブジェクトは、プロバイダーから 1 行のデータを返すコマンドを指定できます。 使用して**レコード**オブジェクトなく**Recordset**を 1 行のデータを返すクエリから結果を受信するオブジェクトが複雑になるほどをインスタンス化のオーバーヘッドが排除**レコード セット**オブジェクト。  
  
 **レコード**オブジェクトできます目的別、従来のリレーショナル データベース以外のデータ ソースのプロバイダーで特になど、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 多くの情報を処理する必要があります内に存在してデータベースでは、テーブルとしてではなくメッセージとして電子メール システムとファイルの最新のファイル システム。 **レコード**と**ストリーム**オブジェクトには、リレーショナル データベース以外のソースに格納された情報へのアクセスが容易にするためです。  
  
 **レコード**オブジェクトが表すし、ディレクトリやファイルなどのデータをファイル システムまたはフォルダー、およびメッセージに、電子メール システムで管理します。 ソースを目的のための**レコード**の開いている現在の行は、 **Recordset**、絶対 URL または相対 URL、開いていると組み合わせて[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
 通常、**レコード セット**コンテナーまたはフォルダーやディレクトリなどの階層で親を表すために使用できます。 A**レコード**ファイルやドキュメントなど、親コンテナーに 1 つのノードに関する特定の情報を返すために使用できます。 主な理由**レコード**この種の情報を表すために使用は、これらのデータ ソースが異種であります。 つまり、各**レコード**別のセットとフィールドの数があります。 従来**レコード セット**データベースから行を含むは同種、行のそれぞれが、同じ数と種類フィールドのことです。  
  
 使用しての詳細については、**レコード**インターネット発行プロバイダーなどのプロバイダーからこの異種データを処理するオブジェクトを参照してください[for Internet Publishing ADO を使用する](../../../ado/guide/data/using-ado-for-internet-publishing.md)です。  
  
## <a name="streams"></a>ストリーム  
 **ストリーム**オブジェクトは読み取り、書き込み、およびバイトのストリームを管理するための手段を提供します。 このバイト ストリームは、テキストまたはバイナリがあり、システム リソースによってのみサイズに制限されます。 通常、ADO**ストリーム**オブジェクトは、次の目的で使用します。  
  
-   データを格納する、 **Recordset** XML 形式で保存します。 これらの XML ストリームからの保存**Recordset**s は、新しいを開くときに、ソースとして使用できます**レコード セット**です。 詳細については、次を参照してください。[ストリームと永続性](../../../ado/guide/data/streams-and-persistence.md)です。  
  
-   含まれている[CommandStreams](../../../ado/reference/ado-api/commandstream-property-ado.md)の代わりに、プロバイダーに対して実行される[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)です。 たとえば、XML アップデート グラムは、SQL Server 用のプロセス、Microsoft OLE DB プロバイダーに対するコマンドのソースとして使用できます。  
  
-   以外の形式で、プロバイダーからの結果を受信する、 **Recordset**、Microsoft OLE DB Provider for SQL Server から XML の結果などです。 詳細については、次を参照してください。[ストリームに結果セットを取得する](../../../ado/guide/data/retrieving-resultsets-into-streams.md)です。  
  
-   テキストまたは構成ファイルまたはメッセージ、通常、for Internet Publishing Microsoft OLE DB プロバイダーなどのプロバイダーで使用するバイトを格納するには この使用の詳細については**ストリーム**、オブジェクトを参照してください[for Internet Publishing ADO を使用する](../../../ado/guide/data/using-ado-for-internet-publishing.md)です。  
  
 A**ストリーム**でオブジェクトを開くことができます。  
  
-   簡単なファイル、URL で指定します。  
  
-   フィールド、**レコード**または**Recordset**を含む、**ストリーム**オブジェクト。  
  
-   既定のストリーム、**レコード**または**Recordset**複合ファイルまたはディレクトリを表すオブジェクト。  
  
-   簡単なファイルの URL を含むリソース フィールドです。  
  
-   すべてでは、特定のソースがありません。 ここで、**ストリーム**オブジェクトがメモリで開いています。 データを書き込み、別に保存し、**ストリーム**またはファイル。  
  
-   BLOB のフィールド、 **Recordset**です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ストリームと永続性](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [コマンド ストリーム](../../../ado/guide/data/command-streams.md)  
  
-   [ストリーム形式で結果セットを取得する](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [インターネットへの発行に ADO を使用する](../../../ado/guide/data/using-ado-for-internet-publishing.md)
