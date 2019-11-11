---
title: セキュリティで保護されたエンクレーブが設定された Always Encrypted を構成して使用する | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: bda4d41d4f2a9c92dca2d41b959ad4c4b32a1c79
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594474"
---
# <a name="configure-and-use-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted を構成して使用する 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[セキュリティで保護されたエンクレーブが設定された Always Encrypted](always-encrypted-enclaves.md) は、既存の [Always Encrypted ](always-encrypted-database-engine.md) 機能を拡張して、データを機密性に保ちながら機密データに対してより高度な機能を有効にすることができます。 この記事では、この機能を構成して使用するための一般的なタスクを示します。

セキュリティで保護されたエンクレーブが設定された Always Encrypted をすぐに使い始める方法がわかるチュートリアルについては、「[チュートリアル: Getting started with Always Encrypted with secure enclaves using SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)」 (チュートリアル: SSMS を使用するセキュリティで保護されたエンクレーブが設定された Always Encrypted の概要) を参照してください。

## <a name="set-up-your-environment-to-support-enclaves-and-attestation"></a>エンクレーブと構成証明をサポートする環境を設定する
詳しくは、次の記事を参照してください。
- [SQL Server で Always Encrypted 用にホスト ガーディアン サービスを設定する](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server)。

## <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted のキーを管理する
詳しくは、以下の記事を参照してください。
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted のキーを管理する - 概要](always-encrypted-enclaves-manage-keys.md)
- [エンクレーブ対応キーをプロビジョニングする](always-encrypted-enclaves-provision-keys.md)
- [エンクレーブ対応キーをローテーションする](always-encrypted-enclaves-rotate-keys.md)

## <a name="configure-columns-with-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted で列を構成する
詳しくは、以下の記事を参照してください。
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用して列の暗号化をインプレースで構成する - 概要](always-encrypted-enclaves-configure-encryption.md)
- [Transact-SQL を使用してインプレースでの列の暗号化を構成する](always-encrypted-enclaves-configure-encryption-tsql.md)
- [既存の暗号化された列に対してセキュリティで保護されたエンクレーブが設定された Always Encrypted を有効にする](always-encrypted-enclaves-enable-for-encrypted-columns.md)

> [!NOTE]
> テスト環境を設定し、SSMS でセキュリティで保護されたエンクレーブが設定された Always Encrypted の機能を試す方法の手順を説明したチュートリアルについては、「[Tutorial: Getting started with Always Encrypted with secure enclaves using SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)」 (チュートリアル: SSMS を使用するセキュリティで保護されたエンクレーブが設定された Always Encrypted の概要) を参照してください。

## <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを実行する
詳しくは、以下の記事を参照してください。
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを実行する - 概要](always-encrypted-enclaves-query-columns.md)
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列のクエリを SSMS で実行する](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="create-and-use-indexes-on-enclave-enabled-columns"></a>エンクレーブ対応の列でインデックスを作成して使用する
詳しくは、以下の記事を参照してください。
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する列でインデックスを作成して使用する](always-encrypted-enclaves-create-use-indexes.md)

## <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用するアプリケーションを開発する
詳しくは、以下の記事を参照してください。
- [セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用するアプリケーションを開発する](always-encrypted-enclaves-client-development.md)
