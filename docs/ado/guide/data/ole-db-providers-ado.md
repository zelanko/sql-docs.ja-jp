---
title: OLE DB プロバイダー (ADO) |Microsoft ドキュメント
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
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 6e0488c3-934d-4976-99dc-65c580dc7a3c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa8bcda85b1b149da9dcc66bed92e044de800f66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-providers-ado"></a>OLE DB プロバイダー (ADO)
OLE DB では、多様な情報源に格納されているデータに一貫したアクセス権を持つアプリケーションを提供する COM インターフェイスのセットを定義します。 これにより、データ ソース、データ ソースに適した DBMS 機能の量をサポートするインターフェイスを介してそのデータを共有することができます。 仕様では、OLE DB の高性能なアーキテクチャを柔軟で、コンポーネント ベースのサービス モデルの使用に基づきます。 アプリケーションとデータ間に中間層の数を指定するのではなく OLE DB だけを必要とするために必要な数のコンポーネントが特定のタスクを実行します。  
  
 たとえば、ユーザーがクエリを実行するとします。 以下のようなシナリオが考えられます。  
  
-   現在存在する ODBC ドライバーがないネイティブの OLE DB プロバイダー、リレーショナル データベースでは、データが存在する: アプリケーションでは、ADO を使用して、OLE DB Provider for ODBC で、適切な ODBC ドライバーを読み込むと対話します。 ドライバーは、SQL ステートメントをデータを取得すると、DBMS に渡します。  
  
-   ネイティブ OLE DB プロバイダーが存在する Microsoft SQL Server で、データが存在する: アプリケーションでは、ADO を使用して、Microsoft SQL Server の OLE DB プロバイダーに直接通信します。 中継ぎ局は必要ありません。  
  
-   データが存在する Microsoft Exchange Server では、OLE DB プロバイダーが SQL クエリの処理エンジンを公開しませんアプリケーションは、ADO、OLE DB Provider for Microsoft Exchange との対話形式を使用してし、OLE DB クエリ プロセッサによってを呼び出します。クエリを処理するコンポーネントです。  
  
-   ドキュメントの形式で Microsoft NTFS ファイル システム内に存在するデータ: 効率的な内容を有効にするファイル システム内のドキュメントのプロパティと内容のインデックスを作成する Microsoft インテックス サービス、経由でネイティブ OLE DB プロバイダーを使用してデータにアクセス検索します。  
  
 前のすべての例では、アプリケーションはデータを照会できます。 コンポーネントの最小数を持つユーザーのニーズが満たされています。 各ケースで必要な場合にのみ、その他のコンポーネントを使用して必要なコンポーネントのみ呼び出されます。 再利用可能なと共有可能なコンポーネントのこの必要に応じた読み込みを OLE DB を使用すると、オブジェクトは大幅に高パフォーマンスに作用します。  
  
 プロバイダーは 2 つのカテゴリに分類されます。 データとサービスを提供するものを提供するものです。 データ プロバイダーは、独自のデータを所有しているし、表形式で、アプリケーションに公開します。 サービス プロバイダーをカプセル化サービスを作成およびデータを利用して、ADO アプリケーションの機能を強化します。 他のコンポーネントまたはサービス プロバイダーと連携して動作する必要があります、サービスのコンポーネントとして、サービス プロバイダーはさらに定義もできます。  
  
 ADO 提供は一貫性のある、さまざまな OLE DB プロバイダーに高レベルのインターフェイスです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [データ プロバイダー](../../../ado/guide/data/data-providers.md)  
  
-   [サービス プロバイダーとコンポーネント](../../../ado/guide/data/service-providers-and-components.md)
