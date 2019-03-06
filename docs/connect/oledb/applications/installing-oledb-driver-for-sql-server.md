---
title: OLE DB Driver for SQL Server のインストール | Microsoft Docs
description: インストールして、SQL Server の OLE DB ドライバーをアンインストールします。
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 288b81c508eed681be190749b5d9618f1f5511ce
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744382"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のインストール
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

SQL Server の OLE DB ドライバーをインストールするには、msoledbsql.msi インストーラーが必要です。
インストーラーを実行し、推奨される項目を選択します。 SQL Server の OLE DB Driver は、Microsoft OLE DB プロバイダーの以前のバージョンとサイドでインストールされているを指定できます。

OLE DB Driver for SQL Server ファイル (msoledbsql.dll、msoledbsqlr.rll) がインストールされている`%SYSTEMROOT%\system32\`します。 さらに、msoledbsql.msi で 32 ビット バイナリをインストールする x64`%SYSTEMROOT%\SysWOW64\`します。

> [!NOTE]  
> OLE DB driver for SQL Server のすべての適切なレジストリ設定は、インストール プロセスの一部として行われます。  

OLE DB Driver for SQL Server ヘッダーとライブラリ ファイル (msoledbsql.h と msoledbsql.lib) がインストールされている`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`します。 さらに、msoledbsql.msi 内の同じファイルのインストール、x64`%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`します。  

Msoledbsql.msi を介して SQL Server 用の OLE DB ドライバーを配布できます。 アプリケーションを展開するときに、SQL Server の OLE DB ドライバーをインストールする必要があります。 チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。 詳細については、「[Visual Studio 2005 用のカスタム ブートストラップ パッケージの作成](https://go.microsoft.com/fwlink/?LinkId=115667)」および「[カスタムの必須コンポーネントの追加](https://go.microsoft.com/fwlink/?LinkId=115668)」をご覧ください。  
  
X64 msoledbsql.msi for SQL Server OLE DB ドライバーの 32 ビット版もインストールされます。 アプリケーションが開発されたアプリケーションの 1 つ以外のプラットフォームを対象とする場合は、msoledbsql.msi x64 および x86 版をダウンロードできます。

msoledbsql.msi を呼び出すと、既定ではクライアント コンポーネントだけがインストールされます。 クライアント コンポーネントは、OLE DB Driver for SQL Server を使用して開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。 例 :  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>サイレント インストール  
 msiexec で /passive、/qn、/qb、または /qr オプションを指定する場合、IACCEPTMSOLEDBSQLLICENSETERMS=YES も指定して、使用許諾契約の条件に同意することを明示的に指定する必要があります。 このオプションは、すべて大文字で指定する必要があります。  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>SQL Server の依存関係として OLE DB ドライバーをインストールします。  
すべての依存アプリケーションがアンインストールされるまで、SQL Server の OLE DB ドライバーをアンインストールする重要です。 ユーザーに、アプリケーションに依存している OLE DB Driver for SQL Server の警告を提供するには、よう、MSI で APPGUID インストール オプションを使用します。  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

APPGUID に渡す値は、特定の製品コードです。 Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。
APPGUID オプションでは、管理者特権でコマンド プロンプトからインストーラーを実行している必要があります。

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
