---
title: リリース ノート - Microsoft ODBC Driver for SQL Server on Linux and macOS |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 14a245264aee998f3707e44d710d422069ef3a8d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Microsoft ODBC Driver for Linux と macOS 上の SQL Server のリリース ノート
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]用 ODBC Driver 17.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows

**追加された機能**:

サポート`SQL_COPT_SS_CEKCACHETTL`と`SQL_COPT_SS_TRUSTEDCMKPATHS`接続属性 (詳細については、次を参照してください[for SQL Server ODBC ドライバーで Always Encrypted を使用して](../using-always-encrypted-with-the-odbc-driver.md))。
- `SQL_COPT_SS_CEKCACHETTL` により、列暗号化キーのローカル キャッシュが存在する、時間を制御するだけでなく、フラッシュ
- `SQL_COPT_SS_TRUSTEDCMKPATHS` により、アプリケーション リストだけを使用して、指定された列マスター_キーの AE 操作を制限するには



読み込みのためのサポート、`.rll`既定の場所から (詳細については、次を参照してください[インストール ドキュメント内のセクションの 'リソース ファイルの読み込み中'](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading))。

[バグの修正](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>新機能、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]の ODBC ドライバーの 17 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux と macOS

**サポートされている新しいディストリビューション**: macOS 高 Sierra および Ubuntu 17.10 

**パフォーマンスの向上**: 10 倍のパフォーマンスが向上する/8/utf-16 からドライバーに変換するときよりも大きいです。

**追加された機能**:

BCP API が常に暗号化されたサポート

新しい接続文字列属性 UseFMTOnly には、一時テーブルを必要とする特殊なケースで以前のメタデータを使用するドライバーが原因です。

Azure SQL のマネージ インスタンス (拡張プライベート プレビュー) をサポートします。 
> [!NOTE]
> さまざまな違いがあるマネージ インスタンスを使用する場合。
> -   FILESTREAM がサポートされていません 
> -   ローカル ファイル システム アクセスはサポートされている、せずに tracefiles などのために必要な 
> -   ローカル コンピューターから UDT を作成するパスはサポートされていません 
> -   Windows 統合認証はサポートされていません 
> -   DTC がサポートされていません 
> -   'sa' アカウントが存在しない (既定のアカウントと呼びます 'cloudSA')
> -   TDS トークン エラー (0xAA) が正しくないサーバー名を返します
> -   データベース名に特殊文字はサポートされていません 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] is not supported
> -   エラー メッセージが英語では、言語に関係なく常に表示される設定 (Azure と同じ) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-linux-and-macos"></a>新機能、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]用 ODBC Driver 13.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux と macOS  

用 ODBC Driver 13.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Always Encrypted と Microsoft SQL Server 2016 と組み合わせて使用する場合は、Azure Active Directory のサポートを追加します。

**新しいディストリビューションがサポートされている**: OS X 10.11 や macOS 10.12 が macOS 上の ODBC ドライバーの最初のリリースでサポートされています。 Ubuntu 16.10 今すぐも加え、サポートが Red Hat 6、7、および SUSE 12 です。 各プラットフォームには、プラットフォームに関連するパッケージ (RPM または DEB) のインストールと構成が容易になります。  参照してください[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)インストール手順についてはします。

**unixODBC Driver Manager 2.3.1 のサポートの変更**:「ODBC ドライバー不要になった unixODBC driver manager については、カスタム パッケージに依存 (RedHat 6 では除く)、代わり UnixODBC の依存関係を解決するのには、配布パッケージ マネージャーには分布のリポジトリ。

**BCP API サポート**: Linux や macOS の ODBC ドライバーが現在の使用をサポート、 [BCP API 関数 (**bcp_init**, などです)。](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>Microsoft ODBC Driver 13.0.< for の新機能[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]on Linux  
SQL Server 用 Microsoft ODBC Driver 13.0.<、SQL Server 2014 および SQL Server 2016 が現在もサポートされます。  

**サポートされている新しいディストリビューション**:

Red Hat、SUSE に加え、Ubuntu のサポートが追加されました。 各プラットフォームには、プラットフォームに関連するパッケージ (RPM または DEB) のインストールと構成が容易になります。  参照してください[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)インストール手順についてはします。

**unixODBC Driver Manager 2.3.1 のサポート**: だけでなく、新しいドライバー マネージャーは、パッケージがあるもインストールと構成を容易にするこの依存関係をインストールするためです。  

**透過的なネットワーク IP 解決**: 透過的なネットワーク IP 解決は、最初がホスト名の ip アドレスがないを解決する場合、ドライバーの接続シーケンスに影響する既存のマルチ サブネット フェールオーバー機能のリビジョン応答し、ホスト名に関連付けられている複数の ip アドレスがあります。

**TLS 1.2 サポート**: Linux に SQL Server 用の Microsoft ODBC ドライバー 13.0.< は、SQL サーバーとのセキュリティで保護された通信を使用して今すぐ TLS 1.2 をサポートします。

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-linux"></a>新機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] on Linux  
ODBC Driver on SUSE Linux (Preview) は、64 ビット SUSE Linux Enterprise 11 Service Pack 2 をサポートします。 詳細については、次を参照してください。[システム要件](../../../connect/odbc/linux-mac/system-requirements.md)です。  

Linux の ODBC ドライバーをサポートしている[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]です。 詳細については、次を参照してください。 [High Availability, Disaster Recovery のサポートを Linux の ODBC ドライバー](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)です。  

ODBC Driver on Linux は、Microsoft Azure SQL Database への接続をサポートします。 詳細については、「 [How to: Connect to Windows Azure SQL Database Using ODBC (方法: ODBC を使用して Windows Azure SQL Database に接続する)](http://msdn.microsoft.com/library/hh974312.aspx)」を参照してください。  

`-l`するオプション (ログイン タイムアウト) が追加されて`bcp`です。 詳細については、次を参照してください。[を使用した接続**bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)です。
