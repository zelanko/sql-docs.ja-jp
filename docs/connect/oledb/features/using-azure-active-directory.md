---
title: Azure Active Directory を使用して |SQL Server 用 Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 44f92e782a497005ea47847301279e4341722d36
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744863"
---
# <a name="using-azure-active-directory"></a>Azure Active Directory の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>用途

18.2.1 バージョン以降、Microsoft OLE DB Driver for SQL Server、OLE DB アプリケーション Azure SQL Database のインスタンスに接続するフェデレーション id を使用できます。 新しい認証方法は次のとおりです。
- Azure Active Directory ログイン ID とパスワード
- Azure Active Directory のアクセス トークン
- Azure Active Directory 統合認証
- SQL ログイン ID とパスワード

> [!NOTE]  
> OLE DB ドライバーを使用した、次の Azure Active Directory オプションを使用している場合ことを確認します。、 [for SQL Server の Active Directory 認証ライブラリ](https://go.microsoft.com/fwlink/?LinkID=513072)がインストールされています。
> - Azure Active Directory ログイン ID とパスワード
> - Azure Active Directory 統合認証
>
> ADAL は、他の認証方法または OLE DB の操作の必要はありません。

> [!NOTE]
> 次の認証モードを使用して`DataTypeCompatibility`(またはその対応するプロパティ) に設定`80`は**いない**サポートします。
> - ログイン ID とパスワードを使用して、azure Active Directory 認証
> - アクセス トークンを使用して、azure Active Directory 認証
> - Azure Active Directory 統合認証

## <a name="connection-string-keywords-and-properties"></a>接続文字列のキーワードとプロパティ
Azure Active Directory 認証をサポートするために、次の接続文字列キーワードが採用されました。

|接続文字列キーワード|接続プロパティ|[説明]|
|---               |---                |---        |
|Access Token|SSPROP_AUTH_ACCESS_TOKEN|Azure Active Directory への認証アクセス トークンを指定します。 |
|[認証]|SSPROP_AUTH_MODE|使用する認証方法を指定します。|

新しいキーワード/プロパティの詳細については、次のページを参照してください。
- [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [初期化プロパティと承認プロパティ](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>暗号化と証明書の検証
このセクションでは、暗号化と証明書の検証動作の変更について説明します。 これらの変更は**のみ**新しい認証またはアクセス トークンの接続文字列キーワード (または対応するプロパティ) を使用する場合に有効です。

### <a name="encryption"></a>暗号化
ドライバー設定することで既定の暗号化値をオーバーライド、新しい接続のプロパティ/キーワードを使用する場合は、セキュリティを強化、`yes`します。 オーバーライドすると、データ ソース オブジェクトの初期化時に発生します。 暗号化は、任意の方法で初期化する前に設定されている場合、値が適用されるため、オーバーライドされていません。

> [!NOTE]   
> 取得するアプリケーションと ADO アプリケーションで、`IDBInitialize`インターフェイスを通じて`IDataInitialize::GetDataSource`、インターフェイスを明示的に実装するコア コンポーネントの既定値に暗号化を設定する`no`します。 新しい認証プロパティ/キーワードがこの設定や、暗号化の値を尊重する結果として、**いない**オーバーライドします。 そのため、**推奨**これらのアプリケーションが明示的に設定する`Use Encryption for Data=true`既定値を上書きします。

### <a name="certificate-validation"></a>証明書の検証
セキュリティを強化する新しい接続のプロパティ/キーワードを尊重、`TrustServerCertificate`設定 (とその対応する接続文字列キーワード/プロパティ)**クライアントの暗号化の設定とは無関係に**します。 その結果、既定でサーバー証明書が検証されます。

> [!NOTE]   
> 証明書の検証を制御することも、`Value`のフィールド、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2`レジストリ エントリ。 有効な値は `0` または `1`です。 OLE DB driver は、レジストリと接続のプロパティ/キーワード設定間で最も安全なオプションを選択します。 ドライバーは、少なくとも 1 つのレジストリ/接続の設定により、サーバー証明書の検証として、サーバー証明書を検証は。

## <a name="gui-additions"></a>GUI の追加
Azure Active Directory 認証を許可するには、ドライバーのグラフィカル ユーザー インターフェイスを拡張されています。 詳細については、以下をご覧ください。
- [SQL Server のログイン ダイアログ](../help-topics/sql-server-login-dialog.md)
- [Universal Data Link (UDL) の構成](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>接続文字列の例
このセクションでは新規および既存の接続の例で使用する文字列のキーワード`IDataInitialize::GetDataSource`と`DBPROP_INIT_PROVIDERSTRING`プロパティ。

### <a name="sql-authentication"></a>SQL 認証
- `IDataInitialize::GetDataSource`の使用
    - 新規:
        > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=SqlPassword**;User ID=[ユーザー名];Password=[パスワード];Use Encryption for Data=true
    - 非推奨: 
        > プロバイダー = MSOLEDBSQL; データ ソース [server] を =; Initial Catalog [データベース] を = です。ユーザー ID [username] を = です。パスワード [password] を = です。データの暗号化を使用して、true を =
- `DBPROP_INIT_PROVIDERSTRING`の使用
    - 新規:
        > Server=[サーバー];Database=[データベース];**Authentication=SqlPassword**;UID=[ユーザー名];PWD=[パスワード];Encrypt=yes
    - 非推奨: 
        > Server=[サーバー];Database=[データベース];UID=[ユーザー名];PWD=[パスワード];Encrypt=yes

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>セキュリティ サポート プロバイダー インターフェイス (SSPI) を使用して、統合 Windows 認証

- `IDataInitialize::GetDataSource`の使用
    - 新規:
        > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
    - 非推奨: 
        > プロバイダー = MSOLEDBSQL; データ ソース [server] を =; Initial Catalog [データベース] を = です。**Integrated Security = SSPI**;データの暗号化を使用して、true を =
- `DBPROP_INIT_PROVIDERSTRING`の使用
    - 新規:
        > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes
    - 非推奨: 
        > サーバー [server] を = です。 データベース [データベース] を = です。**Trusted_Connection = yes**;暗号化 = [はい]

### <a name="aad-username-and-password-authentication-using-adal"></a>ADAL を使用して、AAD のユーザー名とパスワードの認証

- `IDataInitialize::GetDataSource`の使用
    > プロバイダー = MSOLEDBSQL; データ ソース [server] を =; Initial Catalog [データベース] を = です。**Authentication = ActiveDirectoryPassword**;ユーザー ID [username] を = です。パスワード [password] を = です。データの暗号化を使用して、true を =
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryPassword**;UID=[ユーザー名];PWD=[パスワード];Encrypt=yes

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>ADAL を使用して Azure Active Directory 認証の統合

- `IDataInitialize::GetDataSource`の使用
    > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>アクセス トークンを使用して、azure Active Directory 認証

- `IDataInitialize::GetDataSource`の使用
    > プロバイダー = MSOLEDBSQL; データ ソース [server] を =; Initial Catalog [データベース] を = です。**アクセス トークン = [アクセス トークン]**;データの暗号化を使用して、true を =
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > 使用して提供するアクセス トークン`DBPROP_INIT_PROVIDERSTRING`はサポートされていません

## <a name="code-samples"></a>コード サンプル

次のサンプルでは、Azure Active Directory の接続キーワードに接続するために必要なコードを示します。 

### <a name="access-token"></a>Access Token
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    wchar_t accessToken[] = L"eyJ0eXAiOi...";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Access Token=" + accessToken + L";Use Encryption for Data=true;";
    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```
### <a name="active-directory-integrated"></a>Active Directory 統合
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Authentication=ActiveDirectoryIntegrated;Use Encryption for Data=true;";

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr)) 
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```

## <a name="next-steps"></a>次の手順
- [OAuth 2.0 コード付与フローを使用して Azure Active Directory web アプリケーションへのアクセスを承認](https://go.microsoft.com/fwlink/?linkid=2072672)します。

- SQL Server への [Azure Active Directory 認証](https://go.microsoft.com/fwlink/?linkid=2073783)について学習します。

- 使用してドライバーの接続を構成する[接続文字列キーワード](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)OLE DB ドライバーがサポートされます。
