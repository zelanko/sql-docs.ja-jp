---
title: 共通言語ランタイム (CLR) 統合の概要 |Microsoft Docs
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 922489d1145204a4ae5d2dcf8e483149f1b11bcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068462"
---
# <a name="common-language-runtime-integration"></a>共通言語ランタイム統合
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index)ネイティブの共通言語ランタイム (CLR) 統合を使用して、SQL Server のサーバー側モジュール (プロシージャ、関数として .Net 言語を使用して機能の一部を実装できるようにします。トリガー) で変更します。 CLR では、言語間の統合、コード アクセス セキュリティ、オブジェクトの有効期間の管理、デバッグとプロファイルのサポートなどのサービスがマネージド コードに提供されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーやアプリケーション開発者にとっての CLR 統合とは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数 (スカラー関数とテーブル値関数)、ユーザー定義集計関数を記述できるようになることを意味します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、.NET Framework Version 4 が付属します。  

> [!WARNING]
>  CLR では、セキュリティ境界としてサポートされなくなった、.NET Framework のコード アクセス セキュリティ (CAS) が使用されます。 `PERMISSION_SET = SAFE` で作成された CLR アセンブリが、外部のシステム リソースにアクセスし、非管理対象コードを呼び出し、sysadmin 特権を取得できる場合があります。 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 以降、CLR アセンブリのセキュリティを強化するために `clr strict security` という `sp_configure` オプションが導入されました。 `clr strict security` は既定で有効になり、`SAFE` および `EXTERNAL_ACCESS` アセンブリを `UNSAFE` とマークされている場合と同様に扱います。 `clr strict security` オプションは、旧バージョンとの互換性のために無効にできますが、これは推奨されません。 Microsoft では、master データベースで `UNSAFE ASSEMBLY` アクセス許可が付与されている対応するログインを含む証明書または非対称キーで、すべてのアセンブリに署名することをお勧めします。 詳しくは、「[CLR の厳密なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)」をご覧ください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者は、データベース エンジンが信頼するアセンブリのリストにアセンブリを追加することもできます。 詳細については、「[sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)」を参照してください。

## <a name="when-to-use-clr-modules"></a>CLR モジュールを使用する場合ですか。

CLR 統合では、.Net で使用できるは複雑な機能を実装することができます (サーバー、web サービス、データベース) の外部のリソース、カスタム暗号化などにアクセスするため、正規表現などのフレームワークのコードします。サーバー側の CLR 統合の利点を次に示します。
  
-   **優れたプログラミング モデル。** .NET Framework 言語では、以前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の開発者が使用できなかった構造や機能が提供されるので、多くの点で Transact-SQL よりも優れています。 また、開発者は .NET Framework ライブラリの機能も使用できます.NET Framework ライブラリには、プログラミングに関する問題を、迅速かつ効率的に解決する際に使用できる幅広いクラスのセットが用意されています。  
  
-   **強化された安全性とセキュリティ。** マネージ コードは、データベース エンジンによってホストされている共通言語ランタイム環境で実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを利用して、旧バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張ストアド プロシージャに代わる、より安全で確実な機能を提供します。  
  
-   **データ型や集計関数を定義する機能。** ユーザー定義型とユーザー定義集計は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のストレージ機能とクエリ機能を拡張する新しい 2 つのマネージド データベース オブジェクトです。  
  
-   **標準化された環境による効率的な開発。** データベース開発は、今後リリースされる [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio .NET 開発環境に統合されます。 開発者は、データベース オブジェクトやスクリプトの開発およびデバッグを行う際に、中間層またはクライアント層の .NET Framework コンポーネントやサービスを作成する場合と同じツールを使用できます。  
  
-   **強化されたパフォーマンスとスケーラビリティの可能性があります。** .NET Framework 言語のコンパイル モデルと実行モデルは、多くの状況で、Transact-SQL を超える優れたパフォーマンスを提供します。  
  
 このセクションのトピックでは、次の内容について説明します。  
  
 [CLR 統合の概要](../../relational-databases/clr-integration/clr-integration-overview.md)  
 CLR 統合を使用してビルドできるオブジェクトの種類について説明します。また、CLR 統合を使用してデータベース オブジェクトをビルドする場合の要件を確認します。  
  
 [CLR 統合における新機能](../../relational-databases/clr-integration/clr-integration-what-s-new.md)  
 このリリースの新機能について説明します。  
  
 [CLR 統合のアーキテクチャ](https://msdn.microsoft.com/library/05e4b872-3d21-46de-b4d5-739b5f2a0cf9)  
 CLR 統合の設計目標について説明します。  
  
 [CLR 統合の有効化](../../relational-databases/clr-integration/clr-integration-enabling.md)  
 CLR 統合を有効にする方法を説明します。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework のインストール](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみ)   
 [CLR 統合のパフォーマンス](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
  
  
