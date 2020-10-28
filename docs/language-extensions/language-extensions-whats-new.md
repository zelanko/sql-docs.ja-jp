---
title: SQL Server 言語拡張の新機能
titleSuffix: ''
description: 外部言語とデータ プラットフォームの間の統合を拡張、拡大、強化する SQL Server 言語拡張の新機能について説明します。
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1583ab8c54d16d7bcf129e401c2e540fabb342b3
ms.sourcegitcommit: 43b92518c5848489d03c68505bd9905f8686cbc0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155092"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>SQL Server 言語拡張の新機能
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

外部言語とデータ プラットフォーム間の統合が継続的に拡大、拡張、および強化されており、各リリースで[言語拡張](language-extensions-overview.md)機能が SQL Server に追加されています。

## <a name="new-python-and-r-language-extensions-in-sql-server-2019"></a>SQL Server 2019 の Python および R の新しい言語拡張

+ カスタム ランタイムは、[Windows の Python](../machine-learning/install/custom-runtime-python.md) で使用できます。 Linux にインストールするには、[SQL Server on Linux 用の Python カスタム ランタイムのインストール](../machine-learning/install/custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true)に関するページを参照してください

+ カスタム ランタイムは、[Windows の R](../machine-learning/install/custom-runtime-r.md) で使用できます。 Linux にインストールするには、[SQL Server on Linux 用の R カスタム ランタイムのインストール](../machine-learning/install/custom-runtime-r.md?view=sql-server-linux-ver15&preserve-view=true)に関するページを参照してください


## <a name="new-java-language-extension-in-sql-server-2019"></a>SQL Server 2019 の新しい Java 言語拡張

このリリースのすべての機能の詳細については、[SQL Server 2019 の新機能](../sql-server/what-s-new-in-sql-server-ver15.md)に関するページ、および「[SQL Server 2019 のリリース ノート](../sql-server/sql-server-version-15-release-notes.md)」を参照してください。

- Windows および Linux の既定の Java ランタイムは Open Zulu JRE であり、[Windows 上の SQL Server 言語拡張のインストール](install/windows-java.md)と [Linux 上の SQL Server 言語拡張のインストール](../linux/sql-server-linux-setup-language-extensions-java.md)に含まれています。
- サポートされている [Java データ型](how-to/java-to-sql-data-types.md)。
- SQL Server で外部言語 (Java など) を登録するための [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md)。
- [Microsoft 拡張機能 SDK for Java](how-to/extensibility-sdk-java-sql-server.md)。
- Windows および Linux 上では、外部ライブラリで [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) ステートメントを使用して Java コードにアクセスできます。 詳細情報:[SQL Server から Java を呼び出す方法](how-to/call-java-from-sql.md)。
- Windows および Linux 上の [Java 言語拡張](language-extensions-overview.md)。 アクセス許可を割り当て、パスを設定することで、コンパイル済みの Java コードを SQL Server で使用できるようになります。 SQL Server にアクセスできるクライアント アプリでは、[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を呼び出すことで、データを使用し、コードを実行することができます。これは、SQL Server Machine Learning Services 上での R と Python の統合に使用されるものと同じ手順です。

## <a name="next-steps"></a>次のステップ

+ [Windows 上](install/windows-java.md)または [Linux 上に SQL Server 言語拡張をインストール](../linux/sql-server-linux-setup-language-extensions-java.md)します。