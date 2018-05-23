---
title: SQL Server Data Tools (SSDT) での Azure Active Directory のサポート| Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 906bd42a1a4143217a974dd114adf82fa41e7270
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT) での Azure Active Directory のサポート

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md.md](../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

SQL Server Data Tools (SSDT) では、[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) の認証方法がいくつか用意されています。

![SSDT 接続ダイアログ](media/azure-active-directory/interactive.png)

## <a name="active-directory-password-authentication"></a>Active Directory パスワード認証

Active Directory パスワード認証は、Azure Active Directory (Azure AD) の ID を使用して Azure SQL Database に接続するメカニズムです。  Azure とフェデレーションされていないドメインから資格情報を使用して Windows にログインしている場合、あるいは初期ドメインまたはクライアント ドメインに基づく Azure AD を使用する Azure AD 認証を使用している場合は、この方法を使用して接続します。 詳細については、「 [Azure Active Directory 認証を使用して SQL Database に接続する](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication)」を参照してください。  

## <a name="active-directory-integrated-authentication"></a>Active Directory 統合認証

Active Directory 統合認証は、Azure Active Directory (Azure AD) の ID を使用して Azure SQL Database に接続するメカニズムです。 フェデレーション ドメインから Azure Active Directory の資格情報を使用して Windows にログインしている場合は、この方法を使用して接続します。 詳細については、「 [Azure Active Directory 認証を使用して SQL Database に接続する](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication)」を参照してください。

## <a name="active-directory-interactive-authentication"></a>Active Directory 対話型認証

SSDT では、Azure SQL データベースに接続するための新しい認証方法が提供されます - **Active Directory 対話型認証**です。


> [!NOTE]
> Active Directory 対話型認証は、[Visual Studio 2017 バージョン 15.6](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes) の SSDT を使用して接続する場合に利用でき、SSDT を実行するコンピューターに [.NET Framework 4.7.2 がダウンロードまたはインストール](https://www.microsoft.com/net/download/all)されている必要があります。 [.NET Framework 4.7.2](https://docs.microsoft.com/dotnet/api/?view=netframework-4.7.2) がインストールされていない場合、Active Directory 対話型認証のオプションは使用できません。


Active Directory の対話型認証では、Azure Active Directory (AD) の多要素認証 (MFA) を使用して Azure SQL Database で認証することが可能な、対話型の認証がサポートされます。 この方法では、ネイティブ Azure AD ユーザーとフェデレーション Azure AD ユーザー、およびその他のアカウントからのゲスト ユーザー (B2B ユーザーや、@outlook.com、@hotmail.com、@live.com、@gmail.com などの Microsft および Microsoft 以外のアカウントなど) がサポートされます。 この方法が指定される場合、**[ユーザー名]** を指定する必要があり、[パスワード] フィールドが無効になります。 

*Active Directory 対話型認証*で認証する場合、ユーザーが手動でパスワードを入力する必要がある認証ウィンドウが開きます。

![サインイン ダイアログ](media/azure-active-directory/sign-in.png)

MFA の実施は、Azure AD によって、認証プロセス中のこの追加の MFA ポップアップ ウィンドウを通じて提供されます。

> [!NOTE]
> *Active Directory 対話型認証*ではユーザーが手動で (対話的に) パスワードを入力する必要があるため、自動化されたワークフローでの使用はお勧めしません。


## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- *Active Directory 対話型認証*がサポートされるのは、Azure SQL データベースに接続するときのみです。 SQL Server (オンプレミスまたは VM 上) や Azure SQL Data Warehouse に対しては、この認証はサポートされていません。
- *Active Directory 対話型認証*は、*サーバー エクスプローラー*の接続ダイアログではサポートされません。*SQL Server オブジェクト エクスプローラー*で SSDT を使用して接続する必要があります。
- 現在ログインしている Visual Studio アカウントとのシングル サインオン統合は、SSDT ではサポートされません。
- Visual Studio のインストール中に Extensions ディレクトリにインストールされる SQLPackage.exe は、その場所から使用するためのものではありません。 AAD で SQLpackage.exe を使用する場合は、https://www.microsoft.com/en-us/download/details.aspx?id=55088 を参照してください 
- SSDT のデータ比較は、新しい認証方法を含む AAD 認証ではサポートされません。  





## <a name="see-also"></a>参照  
[多要素認証](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[SQL Database での Azure Active Directory 認証](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[Visual Studio の SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[SSDT MSDN フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT チーム ブログ](http://blogs.msdn.com/b/ssdt/)  
[DACFx API リファレンス](https://msdn.microsoft.com/library/dn645454.aspx)  
[SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  
