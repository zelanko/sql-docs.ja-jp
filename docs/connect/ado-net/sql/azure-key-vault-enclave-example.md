---
title: セキュリティで保護されたエンクレーブが設定された Always Encrypted での Azure Key Vault プロバイダーの使用を示す例 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: a4ba44733d2a14323f128f1ab105e79169b90cce
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75250941"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted-enabled-with-secure-enclaves"></a>セキュリティで保護されたエンクレーブが設定された Always Encrypted での Azure Key Vault プロバイダーの使用を示す例

[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-xxxx-md.md)]

この例は、暗号化された列にアクセスするときの Azure Key Vault プロバイダーの使用を示しています。

[!code-csharp [Azure Key Vault Provider with Enclave Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderWithEnclaveProviderExample.cs#1)]

## <a name="see-also"></a>参照

- [Always Encrypted での Azure Key Vault プロバイダーの使用を示す例](azure-key-vault-example.md)
- [チュートリアル:セキュリティで保護されたエンクレーブが設定された Always Encrypted を使用する .NET アプリケーションの開発](tutorial-always-encrypted-enclaves-develop-net-apps.md)」をご覧ください。
- [Always Encrypted と Microsoft .NET Data Provider for SQL Server を使用する](sqlclient-support-always-encrypted.md)
