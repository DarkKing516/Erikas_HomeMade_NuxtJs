<template>

    <body>
        <div class="container-scroller">

            <Navbar />
            <div class="container-fluid page-body-wrapper">

                <Sidebar />
                <div class="main-panel">
                    <div class="content-wrapper">

                        <!-- <slot /> -->
                        <NuxtPage />

                    </div>
                    <Footer />
                </div>
            </div>
        </div>
    </body>
</template>

<script>
export default {
    mounted() {
        // Lista de scripts a cargar
        const scripts = [
            // plugins:js
            'https://code.jquery.com/jquery-3.6.0.min.js',
            'plantillaSkydash/vendors/js/vendor.bundle.base.js',
            // inject:js
            'plantillaSkydash/js/off-canvas.js',
            'plantillaSkydash/js/hoverable-collapse.js',
            'plantillaSkydash/js/template.js',
            'plantillaSkydash/js/settings.js',
            'plantillaSkydash/js/todolist.js',
            // Plugin js for this page
            'plantillaSkydash/vendors/chart.js/Chart.min.js',
            'plantillaSkydash/vendors/datatables.net/jquery.dataTables.js',
            'plantillaSkydash/vendors/datatables.net-bs4/dataTables.bootstrap4.js',
            'plantillaSkydash/js/dataTables.select.min.js',
            // Custom js for this page
            'plantillaSkydash/js/dashboard.js',
            'plantillaSkydash/js/Chart.roundedBarCharts.js'
        ];

        // Función para cargar un script
        function loadScript(src) {
            return new Promise((resolve, reject) => {
                const script = document.createElement('script');
                script.src = src;
                script.onload = resolve; // Resuelve la promesa cuando el script se carga
                script.onerror = reject; // Rechaza la promesa si hay un error
                document.body.appendChild(script);
            });
        }

        // Cargar todos los scripts en secuencia
        scripts.reduce((promise, src) => {
            return promise.then(() => loadScript(src));
        }, Promise.resolve());
    }
};
</script>
<style>
/* <!-- plugins:css --> */
@import '@/public/plantillaSkydash/vendors/feather/feather.css';
@import '@/public/plantillaSkydash/vendors/ti-icons/css/themify-icons.css';
@import '@/public/plantillaSkydash/vendors/css/vendor.bundle.base.css';
/* <!-- Plugin css for this page --> */
@import '@/public/plantillaSkydash/vendors/datatables.net-bs4/dataTables.bootstrap4.css';
@import '@/public/plantillaSkydash/vendors/ti-icons/css/themify-icons.css';
@import '@/public/plantillaSkydash/js/select.dataTables.min.css';
/* <!-- inject:css --> */
@import '@/public/plantillaSkydash/css/vertical-layout-light/style.css';
</style>
