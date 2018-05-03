---
title: SQL Server の OLE DB ドライバーをインストールする |Microsoft ドキュメント
description: インストールして、SQL Server の OLE DB ドライバーをアンインストールしています
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3cb05e6fbbc3507aec67f4faa61f621c4245e7c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーをインストールします。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

SQL Server の OLE DB ドライバーをインストールするには、msoledbsql.msi インストーラーが必要です。
インストーラーを実行し、優先される項目を選択します。 SQL Server の OLE DB Driver は、Microsoft OLE DB プロバイダーの旧バージョンと並列でインストールされているを指定できます。

OLE DB Driver for SQL Server のファイル (msoledbsql.dll、msoledbsqlr.rll) がインストールされている`%SYSTEMROOT%\system32\`です。 Msoledbsql.msi で 32 ビット バイナリをインストールを x64 さらに、`%SYSTEMROOT%\SysWOW64\`です。

> [!NOTE]  
> SQL Server の OLE DB ドライバーのすべての適切なレジストリ設定は、インストール プロセスの一環として行われます。  

OLE DB Driver for SQL Server ヘッダーとライブラリ ファイル (msoledbsql.h および msoledbsql.lib) がインストールされている`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`です。 Msoledbsql.msi 内の同じファイルをインストールする x64 さらに、`%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`です。  

Msoledbsql.msi を介して SQL Server の OLE DB ドライバーを配布できます。 アプリケーションを展開するときに、SQL Server の OLE DB ドライバーをインストールする必要があります。 チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。 詳細については、次を参照してください。 [Visual Studio 2005 用のカスタム ブートス トラップ パッケージの作成](http://go.microsoft.com/fwlink/?LinkId=115667)と[カスタムの必須コンポーネントを追加する](http://go.microsoft.com/fwlink/?LinkId=115668)です。  
  
X64 msoledbsql.msi SQL Server の OLE DB Driver の 32 ビット版もインストールされます。 場合は、アプリケーションでは、上に開発されたもの以外のプラットフォームをターゲットを x64 および x86 msoledbsql.msi のバージョンをダウンロードできます。

Msoledbsql.msi を呼び出すと、クライアント コンポーネントだけが既定でインストールされます。 コンポーネントは、クライアントは、SQL Server の OLE DB Driver を使用して開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。 以下に例を示します。  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>サイレント インストール  
 Msiexec で/passive、/qn、/qb、または/qr オプションを使用する場合は IACCEPTMSOLEDBSQLLICENSETERMS も指定する必要があります = [はい] のエンド ユーザー ライセンス条項に同意することを明示的に指定します。 このオプションは、すべて大文字で指定する必要があります。  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>依存関係として SQL Server の OLE DB ドライバーをインストールします。  
すべての依存アプリケーションがアンインストールされるまで、SQL Server の OLE DB ドライバーをアンインストールする重要です。 SQL Server の OLE DB Driver に依存するアプリケーションの警告をユーザーに提供、とおり、MSI で APPGUID インストール オプションを使用します。  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

APPGUID に渡す値は、特定の製品コードです。 Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。
APPGUID オプションでは、管理者特権でコマンド プロンプトからインストーラーを実行している必要があります。

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
