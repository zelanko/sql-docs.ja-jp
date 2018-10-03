---
title: リリース ノート - Linux および macOS 上の Microsoft ODBC Driver for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 30dffe30bfe0b87156f65d5c21bd0aaba033f0af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746850"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Linux および macOS 上の Microsoft ODBC Driver for SQL Server のリリース ノートです
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Linux および macOS での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新機能

**新しいディストリビューションがサポートされている**: Ubuntu 18.04

**追加された機能**:

Azure SQL Database と SQL Server の詳細については、データの分類を参照してください[データ分類](../data-classification.md)

サーバーの utf-8 エンコードをサポートします。

SQLBrowseConnect

依存関係の動的`libcurl`:
- このバージョンでは、以降、`libcurl`パッケージは、明示的な依存関係ではありません。 `libcurl` OpenSSL または NSS は必要な Azure Key Vault または Azure Active Directory 認証を使用する場合にパッケージ化します。 エラーが発生する場合に関する`libcurl`がインストールされていることを確認します。

ConnectRetryCount と ConnectRetryInterval の接続文字列キーワードでアイドル状態の接続の回復性 (詳細については、次を参照してください。 [Windows ODBC ドライバーの接続レジリエンシー](../windows/connection-resiliency-in-the-windows-odbc-driver.md))。
- 使用`SQL_COPT_SS_CONNECT_RETRY_COUNT`(読み取り専用) の接続試行の数を取得します。
- 使用`SQL_COPT_SS_CONNECT_RETRY_INTERVAL`(読み取り専用) 接続の再試行間隔の長さを取得します。
- 接続は、既定で 1 回再試行されます。


[バグの修正](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Linux and macOS での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新機能

**追加された機能**:

サポート`SQL_COPT_SS_CEKCACHETTL`と`SQL_COPT_SS_TRUSTEDCMKPATHS`接続属性 (詳細については、次を参照してください[ODBC Driver for SQL Server で Always Encrypted を使用して](../using-always-encrypted-with-the-odbc-driver.md))。
- `SQL_COPT_SS_CEKCACHETTL` 列暗号化キーのローカル キャッシュが存在する時間を制御するためにフラッシュできます。
- `SQL_COPT_SS_TRUSTEDCMKPATHS` により、アプリケーションは指定されたリストの列マスター_キーのだけを使用する AE 操作を制限するには



読み込みのサポート、`.rll`既定の場所から (詳細については、次を参照してください[インストール ドキュメントに 'リソース ファイルを読み込んで' セクション](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading))。

[バグの修正](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Linux および macOS での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新機能

**新しいディストリビューションがサポートされている**: macOS High Sierra と Ubuntu 17.10 

**パフォーマンスの向上**: 10 倍のドライバーと UTF-8/16 の間を変換するときにパフォーマンスの向上より大きい。

**追加された機能**:

Always Encrypted のサポートの BCP API

新しい接続文字列属性 UseFMTOnly により一時テーブルを必要とする特殊なケースで、従来のメタデータを使用します。

Azure SQL マネージ インスタンス (延長プライベート プレビュー) をサポートします。 
> [!NOTE]
> マネージ インスタンスを使用する場合は、多くの違いにがあります。
> -   FILESTREAM がサポートされていません 
> -   ローカル ファイル システム アクセスがない、サポートされているが tracefiles などに必要な 
> -   ローカルから UDT を作成するパスはサポートされていません 
> -   Windows 統合認証はサポートされていません 
> -   DTC はサポートされていません 
> -   'sa' アカウントが存在しない (既定のアカウントと呼びます 'cloudSA')
> -   TDS トークン エラー (0xAA) が正しくないサーバー名を返します
> -   データベース名に特殊文字はサポートされていません 
> -   [Dbname1] ALTER DATABASE MODIFY NAME = [dbname2] はサポートされていません
> -   エラー メッセージが英語では、言語に関係なく常に表示される設定 (Azure と同じ) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Linux および macOS での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新機能  

ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Always Encrypted と Microsoft SQL Server 2016 と組み合わせて使用する場合は、Azure Active Directory のサポートを追加します。

**新しいディストリビューションがサポートされている**: OS X 10.11 と macOS 10.12 macOS 上の ODBC ドライバーの最初のリリースでサポートされます。 Ubuntu 16.10 もサポートされます、と共に、Red Hat 6、7、および SUSE 12。 各プラットフォームには、プラットフォームに関連するパッケージ (RPM または DEB) のインストールと構成が容易になります。  参照してください[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)インストール手順についてはします。

**unixODBC Driver Manager 2.3.1 のサポートの変更**: ODBC ドライバーが不要になった unixODBC ドライバー マネージャーのカスタム パッケージに依存 (red Hat 6 を除く)、UnixODBC 依存関係を解決するのには、ディストリビューションのパッケージ マネージャーを代わりに依存していますディストリビューションのリポジトリ。

**BCP API サポート**: Linux と macOS の ODBC ドライバーでは、使用をサポート、 [BCP API 関数 (**bcp_init**など)。](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>新機能については、Microsoft ODBC Driver 13.0 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Linux  
SQL Server 用 Microsoft ODBC Driver 13.0、SQL Server 2014 および SQL Server 2016 が今すぐもサポートされます。  

**新しいディストリビューションがサポートされている**:

Red Hat、SUSE に加え、Ubuntu のサポートが追加されました。 各プラットフォームには、プラットフォームに関連するパッケージ (RPM または DEB) のインストールと構成が容易になります。  参照してください[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)インストール手順についてはします。

**unixODBC Driver Manager 2.3.1 のサポート**: だけでなく、新しいドライバー マネージャー パッケージがあるものインストールと構成を容易にするこの依存関係をインストールします。  

**透過的なネットワーク IP 解決**: 透過的なネットワーク IP 解決は、最初がホスト名の IP を解決する場合、ドライバーの接続シーケンスに影響を与える既存のマルチ サブネット フェールオーバー機能のリビジョン応答し、ホスト名に関連付けられている複数の ip アドレスがあります。

**TLS 1.2 サポート**: の Microsoft ODBC Driver 13.0 for SQL Server on Linux は、SQL Server のセキュリティで保護された通信を使用する場合これで TLS 1.2 をサポートします。

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Linux での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新機能  
ODBC Driver on SUSE Linux (Preview) は、64 ビット SUSE Linux Enterprise 11 Service Pack 2 をサポートします。 詳しくは、「[System Requirements](../../../connect/odbc/linux-mac/system-requirements.md)」(システム要件) をご覧ください。  

Linux 上の ODBC ドライバーは、[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]をサポートしています。 詳細については、次を参照してください。 [ODBC Driver on Linux のサポートの高可用性、ディザスター リカバリー](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)します。  

ODBC Driver on Linux は、Microsoft Azure SQL Database への接続をサポートします。 詳細については、「 [How to: Connect to Windows Azure SQL Database Using ODBC (方法: ODBC を使用して Windows Azure SQL Database に接続する)](http://msdn.microsoft.com/library/hh974312.aspx)」を参照してください。  

`-l`するオプション (ログイン タイムアウト) が追加されました`bcp`します。 詳しくは、「[Connecting with **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)」(bcp による接続) をご覧ください。
