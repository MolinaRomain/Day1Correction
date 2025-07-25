2. Exercice 1 – Dashboard Grafana “Système + App”
2.1 Objectif

Créer un dashboard combinant des métriques système (node_exporter) et métriques applicatives (demo_app), en utilisant la datasource Prometheus déjà pré-configurée.
2.2 Tâches

    Connectez-vous à Grafana (http://localhost:3000, admin/admin).

    Dans Create → Dashboard, créez un dashboard nommé :
    “Système & App Demo”.

    Ajoutez au moins trois panels :

        Panel 1 – CPU Système :
        – Affichez le pourcentage d’utilisation CPU moyen sur 5 minutes.
        – Affichez la légende {{instance}}.

        Panel 2 – Charge CPU App :

        – Affichez la métrique “simulated_cpu_percent” de l’app (simulée toutes les 5 s).
        – Option : changer le type de panel (ligne, gauge ou stat).

        Panel 3 – Taux de requêtes HTTP App pour 1min :

        rate(http_requests_total[1m])

        – Regroupez par method (label) ou affichez toutes méthodes confondues.
        – Utilisez un panel “Time series”.

    Exporter le JSON du dashboard :

        Cliquez sur Share → Export → Save to file.

        Placez ce fichier JSON dans votre dossier TP (ex : dashboards/system_app.json).

4. Exercice 2 – Extension : Alertes métriques de l’app (sans code)
4.1 Objectif

Créer des alertes autour des métriques http_requests_total déjà exposées par l’app, sans modifier l’application elle-même.
4.2 Tâches

    Éditez alert.rules.yml pour ajouter 2 nouvelles règles :

        AppErrorRate : déclenche si plus de 5 % de requêtes renvoient un code 5xx sur 5 min.
        AppTooFewRequests : déclenche si le nombre de requêtes total est inférieur à 1 req/s pendant 10 min.

Exercice 3 : Rajouter des receivers sur alertmanager pour une équipe "dev" et une équipe "infra" --> Créer 2 alertes pour voir si node_exporter est down, si oui faire passer l'alertes dans les 2 receivers "dev" et "infra" et vérifier sur alertmanager

**Envoyer votre dossier (code + dashboard exportés) à molinaromain04@gmail.com, vendredi minuit dernier délai. Objet du mail = Nom + Prénom + TP Prometheus/Grafana**
