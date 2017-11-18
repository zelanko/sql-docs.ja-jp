---
title: "Installing the Driver Manager |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
caps.latest.revision: 59
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ca46eb4fbb6203191a7aace3946daad8361b224
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="installing-the-driver-manager"></a>ドライバー マネージャーのインストール
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックでは、Linux および macOS 上の Microsoft ODBC Driver 11、13、または 13.1 for SQL Server で使用するための unixODBC ドライバー マネージャーをインストールする手順を説明します。  

> [!IMPORTANT]  
> unixODBC ドライバー マネージャーをインストールする前に、お使いのコンピューターにインストールされているドライバー マネージャー パッケージを削除します。 unixODBC ドライバー マネージャーをインストールすると、既存のドライバー マネージャーのエラーが発生する可能性があります。  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-130-and-131"></a>Microsoft ODBC Driver 13.0.< および 13.1 のドライバー マネージャーのインストール
ドライバー マネージャーの依存関係はによって自動的に解決パッケージ管理システムでの指示に従って Linux または macOS 上の SQL Server 用 Microsoft ODBC Driver 13.0.< または 13.1 をインストールすると[Microsoft ODBC Driver をインストールします。Linux または macOS 上の SQL Server の](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。 

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 for SQL Server のドライバー マネージャーのインストール  

(SUSE と Red Hat Linux の場合のみです。)

**インストール スクリプトを使用します。**  
  
> [!IMPORTANT]  
> これらの手順を参照してください`msodbcsql-11.0.2270.0.tar.gz`、Red Hat Linux のインストール ファイルがあります。 SUSE Linux のプレビューをインストールする場合、ファイル名は`msodbcsql-11.0.2260.0.tar.gz`します。  

ドライバー マネージャーをインストールには:  
  
1.  ルートのアクセス許可があることを確認します。  
  
2.  ディレクトリに移動している、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ODBC ドライバーのダウンロードと呼ばれるファイルを配置した`msodbcsql-11.0.2270.0.tar.gz`です。 使用している Linux のバージョンに対応する \*.tar.gz ファイルがあることを確認します。 ファイルを抽出するには、次のコマンドを実行します。 **tar して msodbcsql-11.0.2270.0.tar.gz**です。  

3.  変更、`msodbcsql-11.0.2270.0`ディレクトリがという名前のファイルを表示する必要がありますと`build_dm.sh`です。 実行することができます`build_dm.sh`unixODBC ドライバー マネージャーをインストールします。

4.  使用可能なオプションの一覧を表示するには、次のコマンドを実行します。 **./build_dm.sh--ヘルプ**です。  
  
5.  をインストールする準備ができたら、コンピューターが FTP 経由で外部のサイトにアクセスできる場合は、次のコマンドを実行します。 **./build_dm.sh**です。

お使いのコンピューターが FTP 経由で外部のサイトにアクセスできない場合は、取得`unixODBC-2.3.0.tar.gz`です。 取得することができます`unixODBC-2.3.0.tar.gz`から[http://www.unixodbc.org](http://www.unixodbc.org/)です。クリックして、**ダウンロード**ダウンロード ページに移動するページの左側にリンクします。 適切なリンクをクリックして、unixODBC-2.3.0 (unixODBC-2.3.1 ではなく) をダウンロードします。 unixodbc-2.3.1 はの今回のリリースではサポートされていません、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 UnixODBC ドライバー マネージャーのインストールを開始するには、次のコマンドを実行します。 **./build_dm.sh--ダウンロード url = file://unixODBC-2.3.0.tar.gz**です。  

6.  型**はい**ファイルを解凍を続行します。 プロセスのこの部分が完了までに最大 5 分かかることができます。  

7.  スクリプトの実行が停止したら、画面の指示に従って unixODBC ドライバー マネージャーをインストールします。

これで、ドライバーをインストールする準備ができました。 参照してください[Linux や macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)詳細についてはします。  

**手動インストール**

インストール スクリプトが完了できない場合は、ユーザーが適切なドライバー マネージャーを構成して作成します。

1.  インストールされている古いバージョンの unixODBC (unixODBC 2.2.11 など) を削除します。 Red Hat Enterprise Linux 5 または 6 では、次のコマンドを実行します: **yum 削除 unixODBC**です。 SUSE Linux Enterprise で**zypper 削除 unixODBC**です。  
  
2.  移動して[http://www.unixodbc.org](http://www.unixodbc.org/)です。クリックして、**ダウンロード**ダウンロード ページに移動するページの左側にリンクします。 適切なリンクをクリックして、ファイル unixODBC-2.3.0.tar.gz をコンピューターに保存します。 Unixodbc-2.3.1 はの今回のリリースではサポートされていません、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
3.  Linux コンピューター上のコマンドを実行します:**して unixodbc-2.3.0.tar.gz を tar**です。  
  
4.  unixODBC-2.3.0 ディレクトリに変更します。  
  
5.  コマンド プロンプトでコマンドを実行します: **CPPFLAGS ="-DSIZEOF_LONG_INT 8 を ="**です。  
  
6.  コマンド プロンプトでコマンドを実行します:**エクスポート CPPFLAGS**です。  
  
7.  コマンド プロンプトでコマンドを実行: **"./構成--=/usr--libdir から =/usr/lib64--sysconfdir =/その他 - 有効にする gui のプレフィックス = なし - 有効にするドライバー = なし - 有効にする iconv--と-iconv-char-enc UTF8--と-iconv-ucode-enc を = UTF16LE を ="**.  
  
8.  (ルートとしてログインして)、コマンド プロンプトでコマンドを実行します。**ように**です。  
  
9. (ルートとしてログインして)、コマンド プロンプトでコマンドを実行します。**インストールを行う**です。  

これで、ドライバーをインストールする準備ができました。 参照してください[Linux や macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)詳細についてはします。  
  
## <a name="see-also"></a>参照
[Linux および macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールします。](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

