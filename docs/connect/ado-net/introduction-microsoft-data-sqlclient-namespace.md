---
title: Microsoft.Data.SqlClient 名前空間の概要
description: Microsoft.Data.SqlClient 名前空間の概要ページ。
ms.date: 06/23/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 3a4f0611d3708aba9557deb81ab702f29e7a7462
ms.sourcegitcommit: 22f687e9e8b4f37b877b2d19c5090dade8fa26d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334583"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Microsoft.Data.SqlClient 名前空間の概要

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-20"></a>Microsoft.Data.SqlClient 2.0 のリリース ノート

リリース ノートは、GitHub リポジトリの [2.0 リリース ノート](https://github.com/dotnet/SqlClient/tree/master/release-notes/2.0).

### <a name="breaking-changes"></a>重大な変更

- エンクレーブ プロバイダー インターフェイス `SqlColumnEncryptionEnclaveProvider` のアクセス修飾子が `public` から `internal` に変更されました。

- `SqlClientMetaDataCollectionNames` クラスの定数は、SQL Server の変更を反映するように更新されました。

- ターゲット SQL Server で TLS 暗号化が適用されている場合、ドライバーによってサーバー証明書の検証が実行されるようになりました。これは、Azure の接続では既定です。

- `SqlDataReader.GetSchemaTable()` から、`null` ではなく空の `DataTable` が返されるようになりました。

- ドライバーによる小数点以下桁数の丸めの実行が、SQL Server の動作に一致するようになりました。 下位互換性を維持するために、AppContext スイッチを使用して以前の切り捨ての動作を有効にすることができます。

- **Microsoft.Data.SqlClient** を使用する .NET Framework アプリケーションの場合、以前は `bin\x64` および `bin\x86` フォルダーにダウンロードされた SNI.dll ファイルが `Microsoft.Data.SqlClient.SNI.x64.dll` および` Microsoft.Data.SqlClient.SNI.x86.dll` という名前になり、`bin` ディレクトリにダウンロードされます。

- `SqlConnectionStringBuilder` から接続文字列をフェッチするとき、一貫性を保つために、新しい接続文字列プロパティのシノニムによって古いプロパティが置き換えられます。 [詳細](#new-connection-string-property-synonyms)

### <a name="new-features"></a>新機能

#### <a name="dns-failure-resiliency"></a>DNS エラーの回復性

この機能をサポートする SQL Server エンドポイントへの接続が成功するたびに、ドライバーによって IP アドレスがキャッシュされます。 接続試行中に DNS 解決エラーが発生した場合、ドライバーによって、そのサーバーのキャッシュされた IP アドレス (存在する場合) を使用した接続の確立が試みられます。 

#### <a name="eventsource-tracing"></a>EventSource の追跡

このリリースでは、アプリケーションをデバッグするためのイベント トレース ログのキャプチャに対するサポートが導入されています。 これらのイベントをキャプチャするには、クライアント アプリケーションで SqlClient の EventSource 実装からのイベントをリッスンする必要があります。

```
Microsoft.Data.SqlClient.EventSource
```

詳細については、[SqlClient でイベントのトレースを有効にする](enable-eventsource-tracing.md)方法を参照してください。

#### <a name="enabling-managed-networking-on-windows"></a>Windows でのマネージド ネットワークの有効化

新しい AppContext スイッチ **"Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows"** によって、Windows 上でテストおよびデバッグの目的のためにマネージド SNI 実装を使用できるようになります。 このスイッチを使用すると、Windows 上で .NET Core 2.1 以降のマネージド SNI と .NET Standard 2.0 以降のプロジェクトを使用するようにドライバーの動作が切り替わり、Microsoft.Data.SqlClient ライブラリでネイティブ ライブラリのすべての依存関係が削除されます。

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows", true);
```

ドライバーで使用できるスイッチの完全な一覧については、「[SqlClient の AppContext スイッチ](appcontext-switches.md)」を参照してください。

#### <a name="enabling-decimal-truncation-behavior"></a>小数点の切り捨て動作の有効化 

小数点以下のデータ スケールは、ドライバーによって、既定では SQL Server で行われるように丸められます。 下位互換性を維持するために、AppContext スイッチ **"Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal"** を **true** に設定できます。

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal", true);
```

#### <a name="new-connection-string-property-synonyms"></a>新しい接続文字列プロパティのシノニム

次の既存の接続文字列プロパティに対して新しいシノニムが追加されました。これにより、複数の単語を使用しているプロパティのスペースあけの混乱を回避できます。 古いプロパティ名は下位互換性のために引き続きサポートされますが、[SqlConnectionStringBuilder](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlclient.sqlconnectionstringbuilder) から接続文字列をフェッチすると、新しい接続文字列プロパティが含まれるようになります。

|既存の接続文字列プロパティ|新しいシノニム|
|-----------------------------------|-----------|
| ApplicationIntent | アプリケーションの目的 |
| ConnectRetryCount | Connect Retry Count |
| ConnectRetryInterval | Connect Retry Interval |
| PoolBlockingPeriod | Pool Blocking Period |
| MultipleActiveResultSets | Multiple Active Result Sets |
| MultiSubnetFailover | Multiple Subnet Failover |
| TransparentNetworkIPResolution | Transparent Network IP Resolution |
| TrustServerCertificate | [Trust Server Certificate] |

#### <a name="sqlbulkcopy-rowscopied-property"></a>SqlBulkCopy RowsCopied プロパティ

RowsCopied プロパティを使用すると、実行中の一括コピー操作で処理された行の数に読み取り専用でアクセスできます。 この値は、必ずしもターゲット テーブルに追加された行の最終的な数と同じになるとは限りません。 

#### <a name="connection-open-overrides"></a>接続オープンのオーバーライド

SqlConnection.Open() の既定の動作をオーバーライドして、一時的なエラーによってトリガーされる 10 秒の遅延と自動接続の再試行を無効にすることができます。

```csharp
using SqlConnection sqlConnection = new SqlConnection("Data Source=(local);Integrated Security=true;Initial Catalog=AdventureWorks;");
sqlConnection.Open(SqlConnectionOverrides.OpenWithoutRetry);
```

> [!NOTE]
> このオーバーライドは、SqlConnection.Open() にのみ適用でき、SqlConnection.OpenAsync() には適用できないことにご注意ください。

#### <a name="username-support-for-active-directory-interactive-mode"></a>Active Directory 対話モードでのユーザー名のサポート

.NET Framework と .NET Core の両方に対して Azure Active Directory 対話型認証モードを使用する場合は、接続文字列にユーザー名を指定できます。

**ユーザー ID** または **UID** 接続文字列プロパティを使用してユーザー名を設定します。

```
"Server=<server name>; Database=<db name>; Authentication=Active Directory Interactive; User Id=<username>;"
```

#### <a name="order-hints-for-sqlbulkcopy"></a>SqlBulkCopy の順序のヒント

クラスター化インデックスを持つテーブルに対する一括コピー操作のパフォーマンスを向上させるために、順序のヒントを指定できます。 詳細については、「[の一括コピー操作](sql/bulk-copy-order-hints.md)」セクションを参照してください。

#### <a name="sni-dependency-changes"></a>SNI 依存関係の変更

Windows 上の Microsoft.Data.SqlClient (.NET Core および .NET Standard) は、**Microsoft.Data.SqlClient.SNI.runtime** に依存するようになりました。これにより、**runtime.native.System.Data.SqlClient.SNI** に対する以前の依存関係が置き換えられます。 新しい依存関係によって、Windows で既にサポートされているプラットフォームである ARM64、x64、x86 に加えて、ARM プラットフォームのサポートが追加されます。

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Microsoft.Data.SqlClient 1.1.0 のリリース ノート

リリース ノートは、GitHub リポジトリの [1.1 リリース ノート](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1)でも入手できます。

### <a name="new-features"></a>新機能

#### <a name="always-encrypted-with-secure-enclaves"></a>セキュア エンクレーブを使用する Always Encrypted

Always Encrypted は、Microsoft SQL Server 2016 から使用できます。 セキュリティで保護されたエンクレーブは、Microsoft SQL Server 2019 から使用できます。 エンクレーブ機能を使用するには、必要な構成証明プロトコルと構成証明 URL が接続文字列に含まれている必要があります。 次に例を示します。

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

詳細については、次を参照してください。

- [SqlClient による Always Encrypted のサポート](sql/sqlclient-support-always-encrypted.md)
- [チュートリアル:セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する .NET アプリケーションの開発](sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)」をご覧ください。

## <a name="release-notes-for-microsoftdatasqlclient-10"></a>Microsoft.Data.SqlClient 1.0 のリリース ノート

Microsoft.Data.SqlClient 名前空間の最初のリリースでは、既存の System.Data.SqlClient 名前空間に対する追加機能が提供されます。
リリース ノートは、GitHub リポジトリの [1.0 リリース ノート](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.0)でも入手できます。

### <a name="new-features"></a>新機能

#### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>.NET Framework 4.7.2 System.Data.SqlClient に対する新機能

- **データ分類** - Azure SQL Database および Microsoft SQL Server 2019 で使用できます。

- **UTF-8 のサポート** - Microsoft SQL Server 2019 で使用できます。

#### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>.NET Core 2.2 System.Data.SqlClient に対する新機能

- **データ分類** - Azure SQL Database および Microsoft SQL Server 2019 で使用できます。

- **UTF-8 のサポート** - Microsoft SQL Server 2019 で使用できます。

- **認証** - Active Directory パスワード認証モード。

### <a name="data-classification"></a>データ分類

データ分類では、基になるソースでこの機能がサポートされ、[データの機密性と分類](../../relational-databases/security/sql-data-discovery-and-classification.md)に関するメタデータが含まれている場合に、SqlDataReader 経由で取得したオブジェクトに関するデータの機密性と分類に関する読み取り専用の情報を公開する新しい一連の API が提供されます。 「[SqlClient でのデータ検出と分類](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1)」にあるサンプル アプリケーションを参照してください。

```csharp
public class SqlDataReader
{
    public Microsoft.Data.SqlClient.DataClassification.SensitivityClassification SensitivityClassification
}

namespace Microsoft.Data.SqlClient.DataClassification
{
    public class ColumnSensitivity
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.SensitivityProperty> SensitivityProperties
    }
    public class InformationType
    {
        public string Id
        public string Name
    }
    public class Label
    {
        public string Id
        public string Name
    }
    public class SensitivityClassification
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.ColumnSensitivity> ColumnSensitivities
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.InformationType> InformationTypes
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.Label> Labels
    }
    public class SensitivityProperty
    {
        public Microsoft.Data.SqlClient.DataClassification.InformationType InformationType
        public Microsoft.Data.SqlClient.DataClassification.Label Label
    }
}
```

### <a name="utf-8-support"></a>UTF-8 のサポート

UTF-8 のサポートでは、アプリケーション コードを変更する必要はありません。 これらの SqlClient の変更によって、サーバーで UTF-8 がサポートされ、基になる列の照合順序が UTF-8 である場合に、クライアントとサーバーの間の通信が最適化されます。 [SQL Server 2019 プレビューの新機能](../../sql-server/what-s-new-in-sql-server-ver15.md)の UTF-8 のセクションを参照してください。

### <a name="always-encrypted-with-enclaves"></a>エンクレーブを使用する Always Encrypted

一般に、.NET Framework で System.Data.SqlClient **および組み込み列マスター キー ストア プロバイダー**を使用する既存のドキュメントも .NET Core で動作するようになりました。

 [Always Encrypted と .NET Framework Data Provider を使用して開発する](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted:Windows 証明書ストアで機密データを保護し、暗号化キーを格納する](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>認証

_[認証]_ 接続文字列オプションを使用して、さまざまな認証モードを指定できます。 詳細については、[SqlAuthenticationMethod のドキュメント](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2)を参照してください。

> [!NOTE]
> Azure Key Vault プロバイダーなどのカスタム キー ストア プロバイダーは、Microsoft.Data.SqlClient をサポートするように更新する必要があります。 同様に、エンクレーブ プロバイダーも Microsoft.Data.SqlClient をサポートするように更新する必要があります。
> Always Encrypted は、.NET Framework および .NET Core ターゲットに対してのみサポートされます。 .NET Standard には特定の暗号化依存関係がないため、.NET Standard に対してはサポートされません。
