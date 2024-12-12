---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Xamarin - Binding
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# Xamarin - Binding

Piotr Nowakowski, Paweł Floryan 5P

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Czym jest binding?

**Jest to mechanizm łączenia danych (ang. data binding), który pozwala na synchronizowanie danych pomiędzy kontrolką a źródłem, którym najczęściej jest ViewModel.**

```c#
<Label Text="{Binding Name}" />

```

<div v-click class="text-2xl m-5">
Dzięki temu, gdy zmieniają się dane w ViewModelu, widok (View) jest automatycznie aktualizowany, bez potrzeby ręcznego zarządzania stanem UI. Jest to odpowiednik np. mechaniki useState()
</div>

<br>

<img src="/assets/React-icon.svg.png" v-click class="absolute bottom--35 left-110 opacity-30 transform -rotate-10 transition-fade">

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

img {
  width: 20vw;
  transition: opacity 0.5s ease;
}
</style>

---

## Wyróżniamy kilka trybów bindingu, które definiują w jaki sposób dane będą synchronizowane:

<div v-click class="transition-fade">

|                                        |                                 |
| -------------------------------------- | ------------------------------- |
| <kbd>OneWay</kbd> / <kbd>Default</kbd> | W jedną stronę (domyślna opcja) |
| <kbd>TwoWay</kbd>                      | W dwie strony                   |
| <kbd>OneWayToSource</kbd>              | W jedną stronę ze źródła        |
| <kbd>OneTime</kbd>                     | Tylko raz                       |

</div>

---

# OneWay

<h3> Zmiana w modelu danych powoduje aktualizację widoku, ale zmiany w UI <span v-mark.red="3"> nie są </span> przekazywane do modelu </h3>

<br>
<div v-click class="transition-fade">

```csharp
// xamarin
<Entry Text="{Binding Name, Mode=OneWay}" /> <!-- Zmiana z poziomu ui nie zaktualizuje modelu -->

// kod C#
public string Name { get; set; }

...

Name = "nowa nazwa"; // Zostanie zaktualizowane w ui
```

</div>

---

# TwoWay

<h3> Zmiany w modelu danych i zmiany w UI <span v-mark.red="3"> są synchronizowane </span></h3>

<br>
<div v-click class="transition-fade">

```csharp
// xamarin
<Entry Text="{Binding Name, Mode=OneWay}" /> <!-- Zmiana z poziomu ui zaktualizuje model -->

// kod C#
public string Name { get; set; }

...

Name = "nowa nazwa"; // Zostanie zaktualizowane w ui
```

</div>

---

# OneWayToSource

<h3> Zmiany w UI aktualizują dane w modelu, ale <span v-mark.red="3"> nie ma to wpływu </span>na widok</h3>

<br>
<div v-click class="transition-fade">

```xml
// xamarin
<Entry Text="{Binding Name, Mode=OneWayToSource}" /> <!-- Zmiana z poziomu ui zaktualizuje model -->
```

</div>

---

# OneTime

<h3> Wiązanie danych tylko przy pierwszym załadowaniu widoku (dokładniej reaguje na event zmiany <span v-mark.circle.orange="5">BindingContext</span>). Po wczytaniu danych, <span v-mark.red="3">nie są</span> już synchronizowane. </h3>

<br>
<div v-click class="transition-fade">

```csharp
// xamarin
<Entry Text="{Binding Name, Mode=OneTime}" />

// kod C#
public string Name { get; set; };

public ViewModel() {
    Name = "Warotość początkowa którą obiekt zostanie zainicjowany";
}
```

</div>

---

# Przykładowa aplikacja

<img src="/assets/Xaml.png" v-click class="absolute top-10 left-120 opacity-80 transform transition-fade">
<img src="/assets/Csharp.png" v-click class="absolute left-10 opacity-80 transform transition-fade">

---
layout: center
---

# DEMO

---

# Dziękujemy za uwagę!

## Prezentacja zaprojektowana została z użyciem projektu Slidev.

<br>

# https://github.com/slidevjs/slidev
