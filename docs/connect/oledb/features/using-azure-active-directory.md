---
title: Azure Active Directory | を使用するSQL Server の Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68213556"
---
# <a name="using-azure-active-directory"></a>Azure Active Directory の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>用途

バージョン18.2.1 以降では、Microsoft OLE DB Driver for SQL Server によって、OLE DB アプリケーションはフェデレーション id を使用して Azure SQL Database のインスタンスに接続できるようになります。 新しい認証方法は次のとおりです。
- Azure Active Directory ログイン ID とパスワード
- Azure Active Directory のアクセス トークン
- Azure Active Directory 統合認証
- SQL ログイン ID とパスワード

> [!NOTE]  
> OLE DB ドライバーで次の Azure Active Directory オプションを使用する場合は、 [SQL Server の Active Directory 認証ライブラリ](https://go.microsoft.com/fwlink/?LinkID=513072)がインストールされていることを確認します。
> - Azure Active Directory ログイン ID とパスワード
> - Azure Active Directory 統合認証
>
> ADAL は、他の認証方法や OLE DB 操作には必要ありません。

> [!NOTE]
> 次の認証モード`DataTypeCompatibility` (またはそれに対応するプロパティ) をに設定する`80`ことはサポートされて**いません**。
> - ログイン ID とパスワードを使用して認証を Azure Active Directory する
> - アクセストークンを使用した認証の Azure Active Directory
> - Azure Active Directory 統合認証

## <a name="connection-string-keywords-and-properties"></a>接続文字列のキーワードとプロパティ
Azure Active Directory 認証をサポートするために、次の接続文字列キーワードが導入されました。

|接続文字列キーワード|接続プロパティ|[説明]|
|---               |---                |---        |
|Access Token|SSPROP_AUTH_ACCESS_TOKEN|Azure Active Directory に対して認証するアクセストークンを指定します。 |
|[認証]|SSPROP_AUTH_MODE|使用する認証方法を指定します。|

新しいキーワードおよびプロパティの詳細については、次のページを参照してください。
- [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [初期化プロパティと承認プロパティ](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>暗号化と証明書の検証
このセクションでは、暗号化と証明書検証の動作の変更について説明します。 これらの変更は、新しい認証またはアクセストークンの接続文字列キーワード (またはそれに対応するプロパティ) を使用する場合に**のみ**有効です。

### <a name="encryption"></a>暗号化
セキュリティを強化するために、新しい接続プロパティ/キーワードを使用すると、ドライバーはをに設定する`yes`ことによって既定の暗号化値を上書きします。 オーバーライドは、データソースオブジェクトの初期化時に行われます。 暗号化が何らかの方法で初期化する前に設定されている場合、値は尊重され、オーバーライドされません。

> [!NOTE]   
> ADO アプリケーションや、を通じてインターフェイスを`IDBInitialize`取得する`IDataInitialize::GetDataSource`アプリケーションでは、インターフェイスを実装するコアコンポーネントによって、暗号化`no`が明示的に既定値のに設定されます。 このため、新しい認証プロパティ/キーワードはこの設定を尊重し、暗号化値は上書きされ**ません**。 したがって、これらのアプリケーションは、既定値`Use Encryption for Data=true`をオーバーライドするように明示的に設定することを**お勧め**します。

### <a name="certificate-validation"></a>証明書の検証
セキュリティを強化するために、新しい接続プロパティ/キーワード`TrustServerCertificate`は、**クライアントの暗号化設定**とは関係なく、設定 (および対応する接続文字列のキーワードとプロパティ) を尊重します。 その結果、サーバー証明書は既定で検証されます。

> [!NOTE]   
> 証明書`Value` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2`の検証は、レジストリエントリのフィールドを介して制御することもできます。 有効な値は `0` または `1`です。 OLE DB ドライバーは、レジストリと接続プロパティ/キーワード設定の間で最も安全なオプションを選択します。 つまり、少なくとも1つのレジストリ/接続設定でサーバー証明書の検証が有効になっている限り、ドライバーはサーバー証明書を検証します。

## <a name="gui-additions"></a>GUI の追加
ドライバーのグラフィカルユーザーインターフェイスが拡張され、Azure Active Directory 認証が可能になりました。 詳細については、以下をご覧ください。
- [SQL Server のログイン ダイアログ](../help-topics/sql-server-login-dialog.md)
- [ユニバーサル データ リンク (UDL) の構成](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>接続文字列の例
このセクションでは、および`IDataInitialize::GetDataSource` `DBPROP_INIT_PROVIDERSTRING`プロパティで使用される新規および既存の接続文字列キーワードの例を示します。

### <a name="sql-authentication"></a>SQL 認証
- `IDataInitialize::GetDataSource`の使用
    - 新規:
        > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=SqlPassword**;User ID=[ユーザー名];Password=[パスワード];Use Encryption for Data=true
    - 非推奨:
        > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];User ID=[ユーザー名];Password=[パスワード];Use Encryption for Data=true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    - 新規:
        > Server=[サーバー];Database=[データベース];**Authentication=SqlPassword**;UID=[ユーザー名];PWD=[パスワード];Encrypt=yes
    - 非推奨:
        > Server=[サーバー];Database=[データベース];UID=[ユーザー名];PWD=[パスワード];Encrypt=yes

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>セキュリティサポートプロバイダインターフェイス (SSPI) を使用した統合 Windows 認証

- `IDataInitialize::GetDataSource`の使用
    - 新規:
        > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
    - 非推奨:
        > Provider = MSOLEDBSQL; Data Source = [server]; Initial Catalog = [database];**Integrated Security = SSPI**データの暗号化を使用する = true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    - 新規:
        > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes
    - 非推奨:
        > Server = [server];D データベース = [データベース];**Trusted_Connection = はい**。Encrypt = はい

### <a name="aad-username-and-password-authentication-using-adal"></a>ADAL を使用した AAD のユーザー名とパスワードの認証

- `IDataInitialize::GetDataSource`の使用
    > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=ActiveDirectoryPassword**;User ID=[ユーザー名];Password=[パスワード];Use Encryption for Data=true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryPassword**;UID=[ユーザー名];PWD=[パスワード];Encrypt=yes

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>ADAL を使用した統合 Azure Active Directory 認証

- `IDataInitialize::GetDataSource`の使用
    > Provider=MSOLEDBSQL;Data Source=[サーバー];Initial Catalog=[データベース];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > Server=[サーバー];Database=[データベース];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>アクセストークンを使用して認証を Azure Active Directory する

- `IDataInitialize::GetDataSource`の使用
    > Provider = MSOLEDBSQL; Data Source = [server]; Initial Catalog = [database];**アクセストークン = [アクセストークン]** ;データの暗号化を使用する = true
- `DBPROP_INIT_PROVIDERSTRING`の使用
    > を介し`DBPROP_INIT_PROVIDERSTRING`たアクセストークンの提供はサポートされていません

## <a name="code-samples"></a>コード サンプル

次のサンプルは、接続キーワードを使用して Azure Active Directory に接続するために必要なコードを示しています。 

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

- OLE DB ドライバーがサポートしている[接続文字列キーワード](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)を使用してドライバー接続を構成します。
