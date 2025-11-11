# symfony-7-2025

## Partie 2

Cours de Symfony 7.3 (lors de l'installation) aux WebDev 2025.

## Menu
- [Retour à la partie 1](../README.md)
- [Installation de PHP CS Fixer](#php-cs-fixer)
- [Administration et sécurisation d'un utilisateur](#administration-et-sécurisation-dun-utilisateur)
        - [exercice 8](#exercice-8)
- 

## PHP CS Fixer
Pour formater le code PHP selon les standards PSR-12, vous pouvez utiliser PHP CS Fixer. Voici comment l'installer et l'utiliser dans votre projet Symfony. 

[Documentation officielle](https://cs.symfony.com/).

1. Installez PHP CS Fixer globalement via Composer (si ce n'est pas déjà fait):
   ```bash
    composer require --dev friendsofphp/php-cs-fixer
   ```
Pour l'utiliser, vous pouvez exécuter la commande suivante dans le répertoire de votre projet Symfony :
   ```bash
    ./vendor/bin/php-cs-fixer fix
   ```
Cela analysera et corrigera automatiquement les fichiers PHP de votre projet selon les règles définies par défaut.

Vous pouvez également créer un fichier de configuration `.php-cs-fixer.dist.php` à la racine de votre projet pour personnaliser les règles de formatage. Voici un exemple de configuration basique :
   ```php
    <?php

    $finder = PhpCsFixer\Finder::create()
        ->in(__DIR__.'/src')
        ->in(__DIR__.'/tests');

    return (new PhpCsFixer\Config())
        ->setRules([
            '@PSR12' => true,
            'array_syntax' => ['syntax' => 'short'],
            // Ajoutez d'autres règles selon vos besoins
        ])
        ->setFinder($finder);
   ```

Nous verrons que ça servira à chaque fois que nous écrirons du code dans les prochaines parties. Très utile pour passer les `workflows` **CI/CD** (Continuous Integration/Continuous Delivery) plus tard.

[Retour au menu](#menu)

## Administration et sécurisation d'un utilisateur

Symfony fournit un système robuste pour gérer les utilisateurs et sécuriser les routes de votre application. Voici comment configurer l'administration et la sécurisation d'un utilisateur dans Symfony.

#### Exercice 8

1. **Installation du composant de sécurité** :
   Si ce n'est pas déjà fait, installez le composant de sécurité via Composer :
   ```bash
   composer require symfony/security-bundle
   ```

