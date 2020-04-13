---
title: external scripts enabled サーバー構成オプション | Microsoft Docs
ms.date: 11/13/2017
ms.prod: sql
ms.technology: configuration
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14e3d788034fad9e26f8283e5155d29286ad7360
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664301"
---
# <a name="external-scripts-enabled-server-configuration-option"></a>external scripts enabled サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**適用対象:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] および [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]。

**external scripts enabled** オプションを使用して、特定のリモート言語拡張機能を使用したスクリプトの実行を有効します。 このプロパティは既定で無効になっています。 **Advanced Analytics Services** をインストールするとき、必要に応じてセットアップでこのプロパティを true に設定できます。

## <a name="remarks"></a>解説

[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) プロシージャを使用して外部スクリプトを実行する前に、external script enabled オプションを有効にする必要があります。 R や Python などのサポートされている言語で書かれたスクリプトを実行するには、**sp_execute_external_script** を使います。 

+ [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の場合

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] には、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] での R 言語のサポートと、一連の R ワークステーション ツールおよび接続性ライブラリが含まれます。

    インストール、 **分析の拡張機能の高度な** 機能の中に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R スクリプトの実行を有効に設定します。 R 言語は既定でインストールされます。

+ [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] の場合

    [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] は SQL Server 2016 の場合と同じアーキテクチャを使いますが、Python 言語のサポートを提供します。

    外部スクリプトの実行を有効にするには、 **のセットアップの間に、** Advanced Analytics Extensions[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能をインストールします。 初期セットアップのときに、必ず少なくとも 1 つの言語を選んでください (R と Python のどちらか一方または両方)。 

## <a name="additional-requirements"></a>その他の要件

セットアップの後、外部スクリプトを有効にするには、次のスクリプトを実行します。

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

この変更を有効にするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。

詳しくは、「[Set up SQL Server Machine Learning](../../machine-learning/install/sql-machine-learning-services-windows-install.md)」(SQL Server Machine Learning をセットアップする) をご覧ください。

## <a name="see-also"></a>参照

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)

[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

[SQL Server Machine Learning サービス](../../machine-learning/index.yml)
