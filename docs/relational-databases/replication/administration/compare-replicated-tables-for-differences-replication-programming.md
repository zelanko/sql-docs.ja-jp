---
title: "レプリケートされたテーブルを比較して相違があるかどうかを確認する (レプリケーション プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "tablediff ユーティリティ"
  - "レプリケートされたテーブルの比較"
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# レプリケートされたテーブルを比較して相違があるかどうかを確認する (レプリケーション プログラミング)
  テーブルのアーティクル用にパブリッシュされたデータが、パブリッシャー側とサブスクライバー側とで異なっていると、データが収束しない可能性があります。アーティクルを検証することにより、両者に相違点が存在するかどうかを確認できます。 詳細については、次を参照してください。 [レプリケート データの検証](../../../relational-databases/replication/validate-replicated-data.md)します。 ただし、検証によって返されるのは、一致しているかどうかという情報だけであり、両者のテーブル間の相違について、それ以上詳しい情報は提供されません。  **Tablediff** 詳細なコマンド プロンプト ユーティリティを違いは、2 つのテーブル間の情報と、生成することもできます、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 、パブリッシャー側でデータを収束にサブスクリプションを表示するスクリプトです。  
  
> [!NOTE]  
>   **Tablediff** ユーティリティのみがサポートされて [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サーバーです。  
  
### tablediff を使用してレプリケートされたテーブルを比較し相違点を確認するには  
  
1.  レプリケーション トポロジ内の任意のサーバーでコマンド プロンプトから実行、 [tablediff ユーティリティ](../../../tools/tablediff-utility.md)します。 次のパラメーターを指定します。  
  
    -   **-sourceserver** - データが正しく認識、サーバー、通常はパブリッシャーの名前。  
  
    -   **-sourcedatabase** - 正しいデータを含むデータベースの名前。  
  
    -   **-sourcetable** - 比較対象となるアーティクルのソース テーブルの名前。  
  
    -   (省略可能) **-sourceschema** -既定のスキーマでない場合に、ソース テーブルのスキーマの所有者。  
  
    -   (省略可能) **-sourceuser** と **- sourcepassword** SQL Server 認証を使用してパブリッシャーに接続する場合。  
  
        > [!IMPORTANT]  
        >  可能な場合は、Windows 認証を使用します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する必要がある場合は、セキュリティ資格情報の入力を、ユーザーに対して実行時に求めるようにしてください。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
    -   **-destinationserver** - 通常はサブスクライバーをデータは、比較される、サーバーの名前。  
  
    -   **-destinationdatabase** - の名前、比較対象となるデータベース。  
  
    -   **-destinationtable** - 比較対象となるテーブルの名前。  
  
    -   (省略可能) **-destinationschema** -既定のスキーマかどうか変換先テーブルのスキーマの所有者。  
  
    -   (省略可能) **-destinationuser** と **- destinationpassword** を使用する場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーへの接続を認証します。  
  
        > [!IMPORTANT]  
        >  可能な場合は、Windows 認証を使用します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する必要がある場合は、セキュリティ資格情報の入力を、ユーザーに対して実行時に求めるようにしてください。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
    -   (省略可能)使用 **-c** 列レベルの比較を行う。  
  
    -   (省略可能)使用 **-q** 高速には、行の数、およびスキーマのみの比較します。  
  
    -   (省略可能)ファイル名およびパスを指定 **-o** ファイルに結果を出力します。  
  
    -   (省略可能)結果を挿入するサブスクリプション データベースのテーブルを指定 **-et**します。 テーブルが既に存在する場合は、指定 **-dt** 先テーブルを削除します。  
  
    -   (省略可能)使用 **-f** を生成する、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] パブリッシャーのデータに一致するように、サブスクライバーでデータを修正するファイルです。 使用 **-df** の数を指定する [!INCLUDE[tsql](../../../includes/tsql-md.md)] 各ファイル内のステートメントです。  
  
    -   (省略可能)使用 **-rc** と **-ri** の操作を再試行する間隔を再試行する回数を指定します。  
  
    -   (省略可能)使用 **-strict** 元とコピー先のテーブル間の厳密なスキーマ比較を適用します。  
  
## 参照  
 [サブスクライバーでのデータの検証](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  