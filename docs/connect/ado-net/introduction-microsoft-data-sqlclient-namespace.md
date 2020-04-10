---
title: Microsoft.Data.SqlClient 名前空間の概要
description: Microsoft.Data.SqlClient 名前空間の概要ページ。
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 9a5f787e9cd95e3d2966e5bc2b722aada5b97032
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928994"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Microsoft.Data.SqlClient 名前空間の概要

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Microsoft.Data.SqlClient 1.1.0 のリリース ノート

リリース ノートは、GitHub リポジトリの [1.1 リリース ノート](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1)でも入手できます。

### <a name="new-features"></a>新機能

#### <a name="always-encrypted-with-secure-enclaves"></a>セキュア エンクレーブを使用する Always Encrypted

Always Encrypted は、Microsoft SQL Server 2016 から使用できます。 セキュリティで保護されたエンクレーブは、Microsoft SQL Server 2019 から使用できます。 エンクレーブ機能を使用するには、必要な構成証明プロトコルと構成証明 URL が接続文字列に含まれている必要があります。 例 :

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

詳細については、次のリンクを参照してください。

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

データ分類では、基になるソースでこの機能がサポートされ、[データの機密性と分類](../../relational-databases/security/sql-data-discovery-and-classification.md)に関するメタデータが含まれている場合に、SqlDataReader 経由で取得したオブジェクトに関するデータの機密性と分類に関する読み取り専用の情報を公開する新しい一連の API が提供されます。

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

UTF-8 のサポートでは、アプリケーション コードを変更する必要はありません。 これらの SqlClient の変更は、サーバーで UTF-8 がサポートされ、基になる列の照合順序が UTF-8 である場合に、クライアントとサーバーの間の通信を最適化するだけです。 [SQL Server 2019 プレビューの新機能](../../sql-server/what-s-new-in-sql-server-ver15.md)の UTF-8 のセクションを参照してください。

### <a name="always-encrypted-with-enclaves"></a>エンクレーブを使用する Always Encrypted

一般に、.NET Framework で System.Data.SqlClient **および組み込み列マスター キー ストア プロバイダー**を使用する既存のドキュメントも .NET Core で動作するようになりました。

 [Always Encrypted と .NET Framework Data Provider を使用して開発する](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted:Windows 証明書ストアで機密データを保護し、暗号化キーを格納する](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>認証

_[認証]_ 接続文字列オプションを使用して、さまざまな認証モードを指定できます。 詳細については、[SqlAuthenticationMethod のドキュメント](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2)を参照してください。

> [!NOTE]
> Azure Key Vault プロバイダーなどのカスタム キー ストア プロバイダーは、Microsoft.Data.SqlClient をサポートするように更新する必要があります。 同様に、エンクレーブ プロバイダーも Microsoft.Data.SqlClient をサポートするように更新する必要があります。
> Always Encrypted は、.NET Framework および .NET Core ターゲットに対してのみサポートされます。 .NET Standard には特定の暗号化依存関係がないため、.NET Standard に対してはサポートされません。
